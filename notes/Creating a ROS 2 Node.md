
## Overview

Creating a ROS 2 node consists of three main steps:

1. Set up a workspace and create a package.
2. Implement the node.
3. Build and run the package.

## Workflow

### 1. Create a workspace

Create a ROS 2 workspace and add one or more packages to its `src` directory.

### 2. Create a package

Create either a Python (`ament_python`) or C++ (`ament_cmake`) package.

### 3. Implement the node

- Create a source file.
- Derive your class from [[Node]].
- Implement the desired functionality.
- Register timers, publishers, subscribers, services, or actions if needed.

### 4. Configure the build

- Python: `setup.py`
- C++: `CMakeLists.txt`

### 5. Build the workspace

```bash
colcon build
```

### 6. Source the workspace

```bash
source install/setup.bash
```

### 7. Run the node

```bash
ros2 run <package_name> <executable_name>
```

## Related Concepts

- [[Workspace]]
- [[Package]]
- [[Node]]
- [[Sourcing a Workspace]]