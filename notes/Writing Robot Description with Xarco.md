## Overview

[[Xacro]] helps reduce repetition in robot descriptions, especially when components have the same structure or share dimensions.

## Properties

A property stores a value that can be reused:

```xml
<xacro:property name="wheel_radius" value="0.1" />

<cylinder radius="${wheel_radius}" length="0.05" />
```

## Macros

A macro defines a reusable component. Parameters allow each use to provide different values:

```xml
<xacro:macro name="wheel_link" params="prefix radius">
  <link name="${prefix}_wheel_link">
    <visual>
      <geometry>
        <cylinder radius="${radius}" length="0.05" />
      </geometry>
    </visual>
  </link>
</xacro:macro>

<xacro:wheel_link prefix="left" radius="0.1" />
<xacro:wheel_link prefix="right" radius="0.1" />
```

## Including Files

Robot descriptions can be split across files. For example, a main Xacro file can import macros from `wheel.xacro`:

```xml
<xacro:include filename="wheel.xacro" />

<xacro:wheel_link prefix="left" radius="0.1" />
<xacro:wheel_link prefix="right" radius="0.1" />
```

Xacro also supports mathematical expressions, such as `${pi / 2.0}`, for calculated dimensions and orientations.