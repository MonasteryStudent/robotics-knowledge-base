
## Definition

An action is a communication mechanism in ROS 2 that enables asynchronous client-server communication between [[Node]]s for long-running tasks. It is defined by a name and an action interface. The interface consists of three parts:

- **Goal** – specifies the task to execute.
- **Feedback** – provides progress updates while the goal is being executed.
- **Result** – returned when the goal has finished.

The goal and result are conceptually similar to the request and response of a [[Service]].

## Purpose

It allows a [[Node]] to request a long-running operation from another [[Node]] while continuing to perform other work. During execution, the client can receive progress updates through feedback and a final result once the task has completed. Actions also support goal cancellation.

## Characteristics

- An action is defined by a name and an action interface.
- Both the action client and server must use the same interface.
- An action server can only exist once for a given action name but can handle goals from one or multiple action clients.
- Action clients are only aware of the action name and interface, not of the server node.
- By convention, action names should start with a verb because they represent operations.

## Example

- Navigating a mobile robot to a target position.
- Following a trajectory with a robotic arm.