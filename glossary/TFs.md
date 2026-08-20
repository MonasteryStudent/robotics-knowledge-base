## Definition

In ROS TransForms (TFs) are the [[Transformation]]s between two frames in 3D space.

## Purpose

TFs are used to track the different coordinate frames of a ROS robot over time and describe the spatial relationships between them. A TF therefore contains a timestamp and a transformation, consisting of a translation and rotation, that describes the child frame relative to the parent frame.

## TF Tree

TFs are organized in a tree structure called the TF tree.

Each frame has one parent frame and can have multiple child frames. The tree represents the spatial relationships between all coordinate frames of the robot.

The TF tree can be visualized to verify that the robot model and its frame relationships are configured correctly.

## Create a Tree PDF

You can create a PDF for the TF tree while [[RViz]] is running with the following command:

```bash
ros2 run tf2_tools view_frames
```

## TF Publishing

To specify TFs, you need a robot model defined using [[URDF]]. This robot model can be used by the `robot_state_publisher` node to publish TFs for other packages in the application.