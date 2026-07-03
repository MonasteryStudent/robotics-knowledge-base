## Definition

A topic is a communication channel in ROS 2. It is defined by its name and the type of messages it carries.

## Purpose

It allows [[Node]]s to communicate with each other. Nodes publish data to a topic and receive data by subscribing to it.

## Examples

- Publishing velocity commands to the `/turtle1/cmd_vel` topic to move the turtle.