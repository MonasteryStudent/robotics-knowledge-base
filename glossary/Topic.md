
## Definition

A topic is a named communication channel in ROS 2. It is defined by its name and the interface (data type) of the messages it carries.

## Purpose

It allows [[Node]]s to communicate by exchanging [[Message]]s. [[Publisher]]s send messages to a topic, while [[Subscriber]]s receive them.

## Notes

- A topic is identified by its name and message interface.
- Publishers and subscribers of the same topic must use the same interface.
- Publishers and subscribers are anonymous: they do not know each other directly.
- A node can contain multiple publishers and subscribers.

## Example

- Publishing velocity commands to the `/turtle1/cmd_vel` topic to move the turtle.
- Car node that subscribes to the `radio_98_7` topic and publishes to the `car_location` topic.