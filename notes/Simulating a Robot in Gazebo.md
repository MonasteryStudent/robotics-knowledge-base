## Overview

[[Gazebo]] can be used to test robotic systems in simulation before deploying them to real hardware. A robot can be spawned into a simulated environment, controlled through Gazebo systems, and connected to ROS 2 through `ros_gz_bridge`.

## Robot Simulation Workflow

A typical workflow for simulating a robot in Gazebo is:

1. Create a valid [[URDF]] or [[Xacro]] robot description with all required links and joints.
2. Add physical properties required for simulation:
   - `<inertial>` for mass and inertia.
   - `<collision>` for collision geometry.
3. Start Gazebo and the `robot_state_publisher` node.
4. Spawn the robot into the Gazebo world.
5. Add Gazebo systems using `<plugin>` tags, for example to control a differential-drive robot or publish joint states.
6. Use `ros_gz_bridge` to exchange messages between ROS 2 and Gazebo.

The bridge configuration can be stored in a YAML file.

## Common Package Structure

The robot simulation can be organized across two packages:

```text
my_robot_description/
├── urdf/
│   ├── robot.urdf.xacro
│   └── gazebo-related Xacro files
└── ...
```

`my_robot_description` contains:

- Links and joints.
- Visual geometry.
- Collision geometry.
- Inertial properties.
- Gazebo systems and plugins.

```text
my_robot_bringup/
├── launch/
│   └── my_robot.launch.xml
└── config/
    └── gazebo_bridge.yaml
```

`my_robot_bringup` contains:

- Launch files for starting the application.
- Configuration files for the ROS 2–Gazebo bridge.

## Commands

List all Gazebo topics:

```bash
gz topic -l
```

Show information about a Gazebo topic and its message type:

```bash
gz topic -i -t <topic>
```

Subscribe to a Gazebo topic and output its messages:

```bash
gz topic -e -t <topic>
```

## ROS 2 Integration

Gazebo and ROS 2 use separate communication systems.

The `ros_gz_bridge` package can bridge messages between them.

Example:

```text
ROS 2 /cmd_vel
        ↓
ros_gz_bridge
        ↓
Gazebo /model/my_robot/cmd_vel
```

This allows ROS 2 nodes to control and interact with robots simulated in Gazebo.