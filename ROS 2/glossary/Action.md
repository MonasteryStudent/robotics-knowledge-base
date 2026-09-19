## Definition

An action is a ROS 2 communication mechanism for long-running tasks between [[Node|nodes]]. It uses an asynchronous client-server model: a client sends a goal, may receive feedback during execution, and receives a result when the goal finishes. The client can also request cancellation.