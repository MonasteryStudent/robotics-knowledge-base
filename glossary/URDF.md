## Definition

A Unified Robot Description Format (URDF) file describes the structure and properties of a robot model.

A URDF mainly consists of [[Link|links]] and [[Joint|joints]]:

- A link represents a rigid part of the robot and can contain a visual representation such as a box, cylinder, sphere, or mesh.
- A joint connects two links by defining a parent and child relationship, their relative position, and how they can move relative to each other.

The joints in a URDF define the transformations between the robot's coordinate frames and therefore form the robot's [[TFs|TF tree]].

## Purpose

URDF provides the robot model required to generate TFs and visualize the robot in tools such as [[RViz]].

For larger robot models, [[Xacro]] can be used to make URDF descriptions more reusable and scalable through properties, macros, and multiple files.