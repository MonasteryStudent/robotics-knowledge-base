## Definition

A launch file is a configuration file that defines how one or more [[Node]]s should be started in a ROS 2 system. It can specify nodes, parameters, namespaces, remappings, and other startup configurations.

Launch files can be written in Python, XML, or YAML.

## Purpose

Launch files simplify the startup and configuration of ROS 2 applications by allowing multiple nodes to be launched together with a single command.

They help scale applications by keeping node startup, parameter configuration, namespaces, and remappings in one place.

## Common Structure

Launch files and related configuration files are often stored in a dedicated bringup package.

Example:

```text
turtle_bringup/
├── launch/
│   └── turtle_app.launch.xml
└── config/
    └── turtle_params.yaml
```

## Example

Launching two pairs of `turtlesim` and `turtle_controller` nodes:

```bash
ros2 launch turtle_bringup turtle_app.launch.xml
```

A launch file can also:

- Rename nodes.
- Assign namespaces.
- Remap topics, services, and actions.
- Set parameters individually or load them from a YAML parameter file.
- Include other launch files.