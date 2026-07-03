
## What is `rqt_graph`?

`rqt_graph` is a visualization tool that displays the communication graph of a running ROS 2 system.

## Purpose

It helps to inspect how [[Node]]s communicate with each other by visualizing publishers, subscribers, and the [[Topic]]s between them.

## Usage

```bash
rqt_graph
```

## Example

Running the `talker` and `listener` demo nodes displays a graph showing:

- the two nodes
- the topic used for communication
- the publisher-subscriber relationship