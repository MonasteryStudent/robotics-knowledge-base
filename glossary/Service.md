
## Definition

A service is a communication mechanism in ROS 2 that enables request-response communication between [[Node]]s. It is defined by a name and a service interface. The interface consists of two parts: a request and a response.

## Purpose

It allows a [[Node]] to request a specific operation from another [[Node]] and receive a response. Services are intended for tasks that should be executed once on demand.

## Notes

- A service is based on a **client/server** model.
- A service server provides a service, while one or more clients can send requests to it.
- Both the client and the server must use the same service interface.
- Clients are anonymous. They do not communicate directly with the server node but through the service name and interface.
- A [[Node]] can contain multiple service servers and service clients.

## Example

- Spawning a turtle in `Turtlesim` using the `/spawn` service.