
## Overview

ROS 2 nodes are event-driven.

The `spin()` function keeps a node alive by allowing an executor to wait for events and execute the corresponding callback functions.

## Event Loop

Conceptually, `spin()` behaves like:

```text
while True:

    wait for events

    if topic message:
        topic callback

    if timer expired:
        timer callback

    if service request:
        service callback

    if future completed:
        future callback

    if action goal:
        action callback
```

## Registered Callbacks

ROS 2 does not require the developer to write the main loop.

Instead, the developer registers callback functions for different events.

Examples:

- Topic callback
- Timer callback
- Service callback
- Future callback
- Action callback

## Single-Threaded and Multi-Threaded Executors

By default, callbacks are commonly processed by a single-threaded executor. This means that only one callback can execute at a time.

If a callback takes a long time to complete, it blocks the executor and delays all other callbacks. For example, a long-running action execute callback may prevent the server from processing a cancel request until the goal has already finished.

A multi-threaded executor allows callbacks to be processed using multiple threads. While one callback is still running, another callback can therefore be executed in parallel.

This is useful for long-running operations such as actions, where the server may need to process goal, feedback, or cancel-related callbacks while the goal is being executed.

## Why is this useful?

The node only reacts when an event occurs.

This allows a single node to handle multiple communication mechanisms without manually checking for new messages or requests.

## Multiple Nodes

In the common case, each ROS 2 node runs as an independent process with its own executor started by `spin()`.

However, one executor can also manage multiple nodes within the same process.

**Example**

```text
number_publisher
    └── spin()

number_counter
    └── spin()

reset_counter_client
    └── spin()
```

In this example, each node has its own event loop.

The nodes communicate through ROS 2 communication mechanisms:

```text
number_publisher
        │
        │ Topic: /number
        ▼
number_counter
        │
        │ Service: /reset_counter
        ▲
reset_counter_client
```

**number_publisher**

- Publishes numbers on the `/number` topic.

**number_counter**

- Subscribes to `/number`.
- Counts the received numbers.
- Provides the `/reset_counter` service.

**reset_counter_client**

- Sends a request to the `/reset_counter` service.
- Receives the server's response asynchronously.

## Summary

Each node is responsible for processing its own events.

Depending on the executor, callbacks may be processed sequentially (single-threaded) or in parallel (multi-threaded).

Communication between nodes happens through ROS 2 communication mechanisms such as topics, services, and actions.

## Related Concepts

- [[Node]]
- [[Callback Function]]
- [[Topic]]
- [[Service]]
- [[Action]]