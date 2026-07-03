
## Definition

A launch file is a configuration file that defines how one or more [[Node]]s should be started in a ROS 2 system. It can specify nodes, parameters, remappings, and other startup configurations.

## Purpose

Launch files simplify the startup of ROS 2 applications by allowing multiple nodes and their configurations to be launched with a single command.

## Example

- Launching two `Turtlesim` nodes using:

  ```bash
  ros2 launch turtlesim multisim.launch.py
  ```