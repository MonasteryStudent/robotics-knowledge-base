
## Definition

An action is a communication mechanism in ROS 2 that enables asynchronous communication between [[Node]]s for long-running tasks. It is defined by a name and an action interface. The interface consists of three parts: a goal, feedback, and a result. The goal and result are similar to the request and response of a [[Service]]. Feedback provides progress updates that can be sent by the server while the goal is being executed.

## Purpose

It allows a [[Node]] to request a long-running operation from another [[Node]] while receiving progress updates during execution and a final result when the task is completed.

## Example

- Navigating a mobile robot to a target position.
- Following a trajectory with a robotic arm.