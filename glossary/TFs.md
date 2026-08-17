## Definition

In ROS TransForms (TFs) are the [[Transformation]]s between two frames in 3D space.
## Purpose

TFs are used to track the different coordinate frames of a ROS robot over time. They describe the spatial relationships between frames and are organized into a TF tree.
## TF Publishing

To specify TFs, you need a robot model defined using [[URDF]]. This robot model can be used by the `robot_state_publisher` node to publish TFs for other packages in the application.
