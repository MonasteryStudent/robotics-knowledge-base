
## Overview

ROS 2 topics are used for stream-based communication between [[Node]]s.

A node publishes messages to a topic, and other nodes subscribe to that topic to receive the messages.

## Language Agnostic

ROS 2 communication is independent of the programming language used to implement a node. As long as publishers and subscribers use the same topic name and message interface, they can communicate regardless of whether they are written in Python, C++, or another supported language.

## Communication Middleware

ROS 2 uses DDS (Data Distribution Service) as its communication middleware. DDS enables nodes written in different programming languages to exchange messages as long as they use the same topic name and message interface.

## Important Rules

- A topic is defined by a name and a message interface.
- All publishers and subscribers of a topic must use the same message interface.
- Publishers and subscribers are anonymous and do not know each other directly.
- A node can have multiple publishers and subscribers.

## Typical Use Cases

- Streaming camera images.
- Publishing robot velocity commands.
- Broadcasting sensor measurements.

## Example

A C++ publisher and a Python subscriber communicate through the `/number` topic.