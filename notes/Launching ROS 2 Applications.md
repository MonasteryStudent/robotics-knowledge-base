## Overview

A [[Launch File]] lets you start and configure multiple ROS 2 nodes with a single command.

## Configuration

A launch file can:

- Set node names and namespaces.
- Remap topics, services, and actions.
- Set parameters individually or load them from a YAML file.
- Include other launch files.

## Package Structure

Launch files and related configuration files are often stored in a dedicated bringup package:

```text
turtle_bringup/
├── launch/
│   └── turtle_app.launch.xml
└── config/
    └── turtle_params.yaml
```

## Starting an Application

For example, to launch the application defined in `turtle_app.launch.xml`:

```bash
ros2 launch turtle_bringup turtle_app.launch.xml
```