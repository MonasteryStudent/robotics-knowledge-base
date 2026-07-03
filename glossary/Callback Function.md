
## Definition

A callback function is a function that is registered with ROS 2 and called automatically when a specific event occurs.

## Purpose

Callback functions allow a [[Node]] to react to events such as timer ticks, incoming topic messages, service requests, or action feedback. They are executed while the node is spinning.

## Example

- A timer callback that prints `"Hello"` every second.