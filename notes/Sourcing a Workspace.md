
## What does sourcing do?

Sourcing a workspace updates the current shell environment so that ROS 2 can discover packages, nodes, libraries, and other resources contained in the workspace.

## Purpose

Without sourcing the workspace, ROS 2 only knows the packages installed in `/opt/ros/<distro>`. After sourcing `install/setup.bash`, the current workspace is added to the search paths.