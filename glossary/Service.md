
## Definition

A service is a communication mechanism in ROS 2 that enables request-response communication between [[Node]]s. It is defined by a name and an service interface (data type). The interface consists two parts: a request and a response.

## Purpose

It allows a [[Node]] to request a specific operation from another [[Node]] and receive a response. Services are intended for tasks that should be executed once on demand.

## Example

- Spawning a turtle in `Turtlesim` using the `/spawn` service.