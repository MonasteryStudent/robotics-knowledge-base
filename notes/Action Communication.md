
An action enables asynchronous client-server communication for long-running tasks.

## Communication Flow

```text
Action Client
     │
     │ 1. Send Goal
     ▼
Action Server
     │
     │ 2. Accept or reject the goal
     ▼
Execute Goal
     │
     ├──────────────► Feedback (optional)
     │                 sent while the goal is running
     │
     ├──────────────► Cancel Request (optional)
     │                 from the client
     │
     ▼
Goal Finished
     │
     └──────────────► Result
```

## Steps

1. The action client sends a goal to the action server.
2. The server decides whether to accept or reject the goal.
3. If accepted, the server starts executing the goal.
4. During execution, the server may send feedback messages to the client.
5. The client may send a cancel request while the goal is running.
6. When execution finishes, the server returns the final result.

## Characteristics

- Communication is asynchronous.
- The client is not blocked while the goal is running.
- Feedback allows the client to monitor progress.
- Goals can be cancelled before completion.
- An action server can process goals from one or multiple clients.

## Related Notes

- [[Action]]
- [[Service]]
- [[Topic]]
- [[The Spin Mechanism]]
- [[Multiple Nodes]]