## Definition

Xacro (XML Macros) is a macro language used to create more maintainable and reusable [[URDF]] robot descriptions.

## Purpose

Xacro reduces repetition in URDF files by allowing properties, expressions, and macros to be defined and reused.

It is especially useful for larger robot models with repeated or configurable components.

## Common Features

- Properties for reusable values such as dimensions or colors.
- Macros for reusable robot components.
- Mathematical expressions.
- Parameters for configuring macros.
- Splitting robot descriptions across multiple files.

## Examples

- Property

```xml
<xacro:property name="wheel_radius" value="0.1" />

<cylinder radius="${wheel_radius}" length="0.05" />
```

- Macro

``` XML
<xacro:macro name="wheel_link" params="prefix">

	<link name="${prefix}_wheel_link">
		<visual>
			<geometry>
				<cylinder radius="${wheel_radius}" length="${wheel_length}"  />
			</geometry>
			<origin xyz="0 0 0" rpy="${pi / 2.0} 0 0" />
			<material name="gray" />
		</visual>
	</link>
</xacro:macro>

<xacro:wheel_link prefix="right" />
<xacro:wheel_link prefix="left" />
```

- Including another Xacro file

`wheel.xacro`:

```xml
<?xml version="1.0"?>
<robot xmlns:xacro="http://www.ros.org/wiki/xacro">

	<xacro:macro name="wheel_link" params="prefix">
	    <link name="${prefix}_wheel_link">
	        ...
	    </link>
	</xacro:macro>
	
</robot>
```

`my_robot.urdf.xacro`:

```xml
<?xml version="1.0"?>
<robot name="my_robot" xmlns:xacro="http://www.ros.org/wiki/xacro">
	
	<xacro:include filename="wheel.xacro" />
	
	<xacro:wheel_link prefix="right" />
	<xacro:wheel_link prefix="left" />

</robot>
```