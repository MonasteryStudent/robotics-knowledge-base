
## Overview

ROS 2 is organized into multiple layers. Each layer has a specific responsibility, from the user application down to the communication middleware.

```
Application
    │
rclpy / rclcpp
    │
    rcl
    │
    rmw
    │
   DDS
```

## Layers

### Application

The application contains the ROS 2 nodes written by the developer.

### rclpy / rclcpp

The ROS Client Libraries provide the programming interface for Python and C++. They expose concepts such as [[Node]], [[Publisher]], [[Subscriber]], [[Service]], [[Action]], and timers.

### rcl

The ROS Client Library is the language-independent core used by the language-specific client libraries.

### rmw

The ROS Middleware layer provides an abstraction over different middleware implementations.

### DDS

DDS (Data Distribution Service) is the communication middleware used by ROS 2 to exchange messages between nodes.

## Why is this architecture useful?

The layered architecture separates the application from the communication system.

As a result:

- Nodes can be written in different programming languages.
- Different DDS implementations can be used without changing the application.
- The communication layer is independent of the application logic.