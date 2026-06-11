---
title: "Integrating launch files into ROS 2 packages — ROS 2 Documentation: Jazzy  documentation"
source: "https://docs.ros.org/en/jazzy/Tutorials/Intermediate/Launch/Launch-system.html"
author:
published:
created: 2026-06-11
description:
tags:
  - "clippings"
---
**You're reading the documentation for an older, but still supported, version of ROS 2. For information on the latest version, please have a look at [Lyrical](https://docs.ros.org/en/lyrical/Tutorials/Intermediate/Launch/Launch-system.html).**

## Integrating launch files into ROS 2 packages

**Goal:** Add a launch file to a ROS 2 package

**Tutorial level:** Intermediate

**Time:** 10 minutes

## Prerequisites

You should have gone through the tutorial on how to [create a ROS 2 package](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Creating-Your-First-ROS2-Package.html).

As always, don’t forget to source ROS 2 in [every new terminal you open](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html).

## Background

In the [previous tutorial](https://docs.ros.org/en/jazzy/Tutorials/Intermediate/Launch/Creating-Launch-Files.html), we saw how to write a standalone launch file. This tutorial will show how to add a launch file to an existing package, and the conventions typically used.

## Tasks

### 1 Create a package

Create a workspace for the package to live in:

```
$ mkdir -p launch_ws/src
$ cd launch_ws/src
```

```
$ ros2 pkg create --build-type ament_python --license Apache-2.0 py_launch_example
```

### 2 Creating the structure to hold launch files

By convention, all launch files for a package are stored in the `launch` directory inside of the package. Make sure to create a `launch` directory at the top-level of the package you created above.

For Python packages, the directory containing your package should look like this:

```
src/
  py_launch_example/
    launch/
    package.xml
    py_launch_example/
    resource/
    setup.cfg
    setup.py
    test/
```

To enable colcon to locate and utilize our launch files, we need to inform Python’s setup tools of their presence. To achieve this, open the `setup.py` file, add the necessary `import` statements at the top, and include the launch files into the `data_files` parameter of `setup`:

```python
import os
from glob import glob
# Other imports ...

package_name = 'py_launch_example'

setup(
    # Other parameters ...
    data_files=[
        # ... Other data files
        # Include all launch files.
        (os.path.join('share', package_name, 'launch'), glob('launch/*'))
    ]
)
```

### 3 Writing the launch file

Inside your `launch` directory, create a new launch file called `my_script_launch.xml`. `_launch.xml` is recommended, but not required, as the file suffix for XML launch files.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<launch>
  <node pkg="demo_nodes_cpp" exec="talker" name="talker"/>
</launch>
```

### 4 Building and running the launch file

Go to the top-level of the workspace, and build it:

```
$ colcon build
```

After the `colcon build` has been successful and you’ve sourced the workspace, you should be able to run the launch file as follows:

```
$ ros2 launch py_launch_example my_script_launch.xml
```

## Documentation

[The launch documentation](https://docs.ros.org/en/jazzy/p/launch/architecture.html) provides more details on concepts that are also used in `launch_ros`.

Additional documentation/examples of launch capabilities are forthcoming. See the source code ([https://github.com/ros2/launch](https://github.com/ros2/launch) and [https://github.com/ros2/launch\_ros](https://github.com/ros2/launch_ros)) in the meantime.

---
### 🔗 Development Workflow & Tooling
[[Using colcon to build packages — ROS2-Jazzy.md|Using colcon to build packages]], [[Creating a workspace — ROS2-Jazzy.md|Creating a workspace]], [[Creating a package — ROS2-Jazzy.md|Creating a package]], [[Creating a launch file — ROS2-Jazzy.md|Creating a launch file]], [[Managing Dependencies with rosdep — ROS2-Jazzy.md|Managing Dependencies with rosdep]], [[Configuring environment — ROS2-Jazzy.md|Configuring environment]]
