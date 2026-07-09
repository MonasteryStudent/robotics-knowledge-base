
## Overview

ROS 2 provides many predefined interfaces. If none of them matches the requirements of an application, custom interfaces can be created.

As a best practice, all custom interfaces should be placed in a dedicated interface package.

## Interface Package

Create a dedicated package for custom interfaces.

Recommendations:

- Use `ament_cmake` as the build type.
- Store only interfaces in this package (no nodes or other source code).
- Name the package using the application or robot name followed by `_interfaces`.

Example:

```text
my_robot_interfaces
```

## Creating a Message Interface

1. Create a `.msg` file inside the `msg/` directory.
2. Define the message fields using built-in types or existing message types.
3. Register the interface in `CMakeLists.txt`.
4. Build the interface package.
5. Source the workspace.

## Using a Custom Interface

After building the interface package, the generated interface can be imported just like any built-in ROS 2 interface.

Python:

```python
from my_robot_interfaces.msg import HardwareStatus
```

C++:

```cpp
#include "my_robot_interfaces/msg/hardware_status.hpp"
```

## Best Practices

- Check whether an existing interface already satisfies your requirements before creating a new one.
- Keep all custom interfaces in a dedicated interface package.
- Reuse interfaces across multiple nodes and packages.