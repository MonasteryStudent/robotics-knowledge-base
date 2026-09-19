## Overview

[[TFs]] allow ROS 2 components to track the spatial relationships between a robot's coordinate frames over time.

## TF Tree

Connected frames form a TF tree. Each child frame has one parent frame and can have multiple child frames of its own.

Inspecting the tree helps verify that the robot's frame relationships are configured as intended.

## Publishing TFs

A robot model defined using [[URDF]] can be used by the `robot_state_publisher` node to publish transforms between the robot's frames.

## Inspecting the Tree

Generate a PDF showing the frame relationships:

```bash
ros2 run tf2_tools view_frames
```