
## Overview

In the common case, each ROS 2 node runs as an independent process with its own event loop started by `spin()`.

The nodes do not share a common main loop. Instead, each node waits for events independently and executes its own callback functions.

## Example

Consider the following three nodes:

```text
number_publisher
    └── spin()

number_counter
    └── spin()

reset_counter_client
    └── spin()
```

Each node has its own event loop.

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

### number_publisher

- Publishes numbers on the `/number` topic.

### number_counter

- Subscribes to `/number`.
- Counts the received numbers.
- Provides the `/reset_counter` service.

### reset_counter_client

- Sends a request to the `/reset_counter` service.
- Receives the server's response asynchronously.

## Summary

Each node is responsible for processing its own events.

Communication between nodes happens through ROS 2 communication mechanisms such as topics, services, and actions, while every node continues to run its own event loop independently.