## Overview

A Thread is an execution path within a process. Multiple threads in the same process share memory and can therefore access the same variables and objects.

- **Concurrency**: multiple tasks can make progress during overlapping periods of time.
- **Parallelism**: multiple tasks are executed at the same time on different threads or CPU cores.
- **Race Condition**: the result depends on the timing and order in which multiple threads access shared state.
- **Lock**: protects a critical section so that only one thread can execute it at a time.

For example, an operation such as:

```python
counter += 1
```

conceptually consists of reading the value, modifying it, and writing it back. If two threads interleave these steps unfavorably, an update can be lost.

## Async vs. Threading

`async` / `await` is not the same as threading.

When an asynchronous function reaches:

```python
result = await completion_future
```

it can suspend its execution without blocking the executor thread. While the coroutine is waiting, the same thread can execute other callbacks.

This provides Concurrency without necessarily providing Parallelism.

## Relation to the ROS 2 Action Server

The navigation Action Server uses shared state such as:

```python
self.active_goal_handle
self.active_goal_future
self.goal_queue
self.state
self.target_x
self.target_y
self.current_x
self.current_y
self.current_yaw
```

With a Multi-Threaded Executor, several callbacks could access this state at the same time. This can introduce race conditions.

For example, `execute_callback()` and `control_callback()` could both modify `active_goal_handle` or the goal queue. Similarly, `odom_callback()` and `control_callback()` could overlap, causing the controller to read a mixture of old and new pose values.

## Current Architecture

The current server uses:

- a Single-Threaded Executor through `rclpy.spin(node)`
- an asynchronous `execute_callback()`
- a Future awaited with `await completion_future`
- a timer-based state machine
- a Reentrant Callback Group

A Reentrant Callback Group does **not** create threads. It only allows callbacks in the same group to overlap logically. Whether callbacks can actually run in parallel depends on the Executor.

With the current single-threaded executor, only one callback executes at a time. This makes shared state easier to manage and currently avoids the need for explicit locks.

## Why the Previous Version Needed Multiple Threads

The earlier `execute_callback()` contained a blocking `while` loop.

With a Single-Threaded Executor, this loop would have prevented callbacks such as `odom_callback()` and the timer callback from running.

The current architecture avoids this:

```text
execute_callback()
    ↓
await completion_future
    ↓
executor thread is free
    ↓
control_callback() / odom_callback()
    ↓
future is completed
    ↓
execute_callback() resumes
```

This allows the action server to remain responsive without a blocking control loop and without requiring an additional executor thread.

## Key Idea

```text
async / await
→ one thread can alternate between multiple tasks

threading
→ multiple threads can execute tasks at the same time

Executor
→ decides how ROS 2 callbacks are scheduled and on which threads they run

Callback Group
→ defines which callbacks are allowed to overlap

shared state + multiple threads
→ possible race conditions → synchronization may be required
```
