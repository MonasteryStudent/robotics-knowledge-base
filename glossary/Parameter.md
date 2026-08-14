## Definition

A parameter is a configurable value associated with a [[Node]]. Each parameter has a name, a data type, and a value.

## Purpose

Parameters allow the behavior of a [[Node]] to be configured without modifying its source code. They can be set before or during runtime, depending on the implementation of the node.

## Setting Parameters at Startup

Parameters can be passed to a node when it is started using ROS 2 command-line arguments.

Example:

``` bash
ros2 run turtle_controller_py turtle_controller \
  --ros-args \
  -p color_left:=yellow \
  -p turtle_velocity:=1.5
```

The `-p` option is used to assign a value to a parameter.

## Parameter Configuration Files

ROS 2 parameters can be loaded from YAML configuration files. This allows
multiple parameter values to be stored and reused instead of passing them
individually through command-line arguments.

Example:

``` yaml
/turtle_controller:
  ros__parameters:
    color_left: yellow
    color_right: purple
    turtle_velocity: 1.5
```

The parameter file can be loaded when starting the node:

``` bash
ros2 run turtle_controller_py turtle_controller \
  --ros-args \
  --params-file config/turtle_controller_params.yaml
```

The node name in the YAML file must match the node for which the parameters should be loaded.

## Changing Parameters at Runtime

Parameters can also be changed while a node is running:

``` bash
ros2 param set /turtle_controller turtle_velocity 2.0
```

A node can register a parameter callback to validate and react to parameter changes at runtime. An on-set parameter callback can reject invalid parameter values before they are applied.