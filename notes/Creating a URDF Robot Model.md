## Overview

When building a robot model with [[URDF]], start with a single base link, usually named `base_link`.

Each additional link is connected to an existing link through a joint. A robot model therefore grows step by step as a tree of links connected by joints.

A good workflow is to add and validate only one link and one joint at a time.

## Workflow

### 1. Add a New Link

Add a new `<link>` element to the URDF.

Initially, set the origin values of the link's visual elements to zero:

```xml
<origin xyz="0 0 0" rpy="0 0 0" />
```

This keeps the initial model simple while the relationship between the links is established.

### 2. Connect the Link with a Joint

Add a new `<joint>` element that connects the new link to an existing link.

A joint requires:

- A parent link
- A child link
- A joint type
- An origin

Example:

```xml
<joint name="example_joint" type="fixed">
    <parent link="base_link" />
    <child link="new_link" />
    <origin xyz="0 0 0" rpy="0 0 0" />
</joint>
```

The parent is an existing link in the robot model, while the child is the newly added link. When you are more experienced you can already set the correct movement type of the joint. For the beginning always default to `fixed` until step three.

### 3. Determine the Joint Origin

The joint origin defines where the coordinate frame of the child link is located relative to the frame of the parent link.

Start with the origin set to zero and adjust it step by step.

Use [[RViz]] to inspect the frames and determine where the child frame should be located relative to its parent.

It can be useful to temporarily disable the visual representation of the new link so that the coordinate frames can be inspected more clearly.

### 4. Configure Joint Movement

If the joint allows movement, configure the appropriate joint type.

Depending on the joint type, additional properties may be required, such as:

- Axis of rotation or translation
- Joint limits
- Position limits
- Velocity limits
- Effort limits

### 5. Adjust the Visual Origin

Once the joint origin and therefore the child frame are correct, adjust the visual origin of the child link.

The visual origin defines where the geometry is located relative to the link's own coordinate frame.

This means there are two different relationships to keep in mind:

```text
Joint origin
    → position of the child frame relative to the parent frame

Visual origin
    → position of the geometry relative to its own link frame
```

After adjusting the visual origin, verify the result again in [[RViz]].

## Important Guidelines

- Add only one link and one joint at a time.
- Fully validate a new connection before adding the next link.
- Avoid changing the origin of previously validated parent links.
- If an existing link needs to be corrected, temporarily disable or remove its children and work outward from that link again.
- A link can have multiple child links, but only one parent link.
- Change one origin value at a time and verify the result in [[RViz]].
- Use the [[TFs|TF]] tree to verify that the relationships between the robot's frames are correct.

## Relationship Between URDF and TF

A URDF describes the structure of the robot using links and joints.

The joints define the relationships between the coordinate frames of the links. These relationships can then be used to generate [[TFs]].

A simplified workflow is:

```text
URDF
  ↓
Links + Joints
  ↓
robot_state_publisher
  ↓
TF tree
  ↓
RViz / other ROS nodes
```

## References

- [URDF XML – Link](https://wiki.ros.org/urdf/XML/link)
- [URDF XML – Joint](https://wiki.ros.org/urdf/XML/joint)