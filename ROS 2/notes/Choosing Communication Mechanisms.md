## Overview

ROS 2 provides different communication mechanisms. Each mechanism is designed for a specific type of communication.

## Comparison

| Feature | [[Topic]] | [[Service]] | [[Action]] |
|----------|-----------|-------------|------------|
| Communication Model | Publish/Subscribe | Client/Server | Client/Server |
| Communication Direction | Unidirectional | Bidirectional | Bidirectional |
| Execution Time | Continuous | Short | Long-running |
| Acknowledgement | ❌ | ✅ | ✅ |
| Feedback | ❌ | ❌ | ✅ |
| Cancel | ❌ | ❌ | ✅ |
| Typical Use Case | Sensor data, command streams | Quick operations | Long-running operations |

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

## Actions

Use [[Action]]s when a [[Node]] should execute a **long-running** operation while allowing the client to receive progress updates and optionally cancel the goal.

Actions use a client/server model with **bidirectional** communication.

Typical examples:

- Navigating a mobile robot to a target position
- Following a trajectory with a robotic arm

## Design Considerations

Choosing the appropriate communication mechanism depends primarily on:

- Whether communication is continuous or request-based.
- Whether a response is required.
- Whether the operation is short or long-running.
- Whether progress updates or cancellation are needed.