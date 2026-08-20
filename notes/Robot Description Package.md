## Overview

A robot description package contains the files required to describe, visualize, and publish the state of a robot model in ROS 2.

A typical package uses the `_description` suffix, for example:

```text
my_robot_description/
├── CMakeLists.txt
├── package.xml
├── launch/
│   ├── display.launch.py
│   └── display.launch.xml
├── meshes/
├── rviz/
│   └── urdf_config.rviz
└── urdf/
    ├── common_properties.xacro
    ├── mobile_base.xacro
    └── my_robot.urdf.xacro
```

## Important Nodes

### `robot_state_publisher`

The `robot_state_publisher` node publishes the robot's TFs based on two main inputs:

- The robot model provided through the `robot_description` parameter.
- The current joint states received on the `/joint_states` topic.

The robot model is usually defined using [[URDF]] or [[Xacro]].

### `joint_state_publisher_gui`

The `joint_state_publisher_gui` node can be used to manually change the values of movable joints.

It publishes these joint states on the `/joint_states` topic.

This node is mainly useful for testing and visualization. On a real robot, joint states are typically provided by the robot hardware or its controllers.

### `rviz2`

[[RViz]] can be used to visualize the robot model and its coordinate frames.

## Data Flow

```text
URDF / Xacro
     ↓
robot_description parameter
     ↓
robot_state_publisher
     ↑
/joint_states
     ↑
joint_state_publisher_gui

robot_state_publisher
     ↓
TFs
     ↓
RViz
```

## Common Package Structure

- `urdf/` — URDF and Xacro files describing the robot model.
- `meshes/` — mesh files used by robot links.
- `rviz/` — saved RViz configurations.
- `launch/` — launch files for starting the robot description and visualization.
- `package.xml` — package metadata and dependencies.
- `CMakeLists.txt` — build and installation configuration.