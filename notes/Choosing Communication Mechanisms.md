
## Overview

ROS 2 provides different communication mechanisms. Each mechanism is designed for a specific type of communication.

## Topics

Use [[Topic]]s for continuous, **unidirectional** data streams.

In unidirectional communication, messages flow in only one direction: from a [[Publisher]] to one or more [[Subscriber]]s. Subscribers receive messages but do not send a response.

Typical examples:

- Publishing sensor data
- Sending velocity commands to a robot
- Broadcasting status information

## Services

Use [[Service]]s when a [[Node]] should perform a specific operation on demand and return a response.

Services use a client/server model with **bidirectional** communication: a client sends a request, and the server returns a response.

Typical examples:

- Enable or disable a motor
- Start or stop a robot
- Perform a quick computation

## Design Considerations

Choosing the appropriate communication mechanism depends on the application.

In many cases the choice is straightforward, but some situations require careful design decisions.