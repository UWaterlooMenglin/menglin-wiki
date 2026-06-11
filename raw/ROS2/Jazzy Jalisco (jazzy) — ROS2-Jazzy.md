---
title: "Jazzy Jalisco (jazzy) — ROS 2 Documentation: Jazzy  documentation"
source: "https://docs.ros.org/en/jazzy/Releases/Release-Jazzy-Jalisco.html"
author:
published:
created: 2026-06-08
description:
tags:
  - "clippings"
---
**You're reading the documentation for an older, but still supported, version of ROS 2. For information on the latest version, please have a look at [Lyrical](https://docs.ros.org/en/lyrical/Releases/Release-Jazzy-Jalisco.html).**

## Jazzy Jalisco (jazzy)

*Jazzy Jalisco* is the tenth release of ROS 2. What follows is highlights of the important changes and features in Jazzy Jalisco since the last release. For a list of all of the changes since Iron, see the [long form changelog](https://docs.ros.org/en/jazzy/Releases/Jazzy-Jalisco-Complete-Changelog.html)

## Supported Platforms

Jazzy Jalisco supports the following platforms according to [the platform support tiers](https://docs.ros.org/en/jazzy/The-ROS2-Project/Platform-Support-Tiers.html):

Tier 1 platforms:

- Ubuntu 24.04 (Noble): `amd64` and `arm64`
- Windows 10 (Visual Studio 2019): `amd64`

Tier 2 platforms:

- RHEL 9: `amd64`

Tier 3 platforms:

- macOS: `amd64`
- Debian Bookworm: `amd64`

Targeted platforms:

| Architecture | Ubuntu Noble (24.04) | Windows 10 (VS2019) | RHEL 9 | Ubuntu Jammy (22.04) | macOS | Debian Bookworm (12) | OpenEmbedded / Yocto Project |
| --- | --- | --- | --- | --- | --- | --- | --- |
| amd64 | Tier 1 \[d\]\[a\]\[s\] | Tier 1 \[a\]\[s\] | Tier 2 \[d\]\[a\]\[s\] | Tier 3 \[s\] | Tier 3 \[s\] | Tier 3 \[s\] | Tier 3 \[s\] |
| arm64 | Tier 1 \[d\]\[a\]\[s\] |  |  |  |  | Tier 3 \[s\] | Tier 3 \[s\] |
| arm32 | Tier 3 \[s\] |  |  |  |  | Tier 3 \[s\] | Tier 3 \[s\] |

The following indicators show what delivery mechanisms are available for each platform.

" \[d\] " Distribution-specific (Debian, RPM, etc.) packages will be provided for this platform for packages submitted to the rosdistro.

" \[a\] " Binary releases are provided as a single archive per platform containing all packages in the Jazzy ROS 2 repos file\[^13\].

" \[s\] " Compilation from source.

Middleware Implementation Support:

| Middleware Library | Middleware Provider | Support Level | Platforms | Architectures |
| --- | --- | --- | --- | --- |
| rmw\_fastrtps\_cpp\* | eProsima Fast-DDS | Tier 1 | All Platforms | All Architectures |
| rmw\_cyclonedds\_cpp | Eclipse Cyclone DDS | Tier 1 | All Platforms | All Architectures |
| rmw\_connextdds | RTI Connext | Tier 1 | Ubuntu, Windows, and macOS | All Architectures except arm64 |
| rmw\_fastrtps\_dynamic\_cpp | eProsima Fast-DDS | Tier 2 | All Platforms | All Architectures |
| rmw\_gurumdds\_cpp | GurumNetworks GurumDDS | Tier 3 | Ubuntu and Windows | All Architectures except arm32 |

" \* " means default RMW implementation.

Middleware implementation support is dependent upon the platform support tier. For example a Tier 1 middleware implementation on a Tier 2 platform can only receive Tier 2 support.

Minimum language requirements:

- C++17
- Python 3.8

Dependency Requirements:

<table><thead><tr><th></th><th colspan="2"><p>Required Support</p></th><th colspan="5"><p>Recommended Support</p></th></tr><tr><th><p>Package</p></th><th><p>Ubuntu Noble</p></th><th><p>Windows 10**</p></th><th><p>RHEL 9</p></th><th><p>Ubuntu Jammy</p></th><th><p>macOS**</p></th><th><p>Debian Bookworm</p></th><th><p>OpenEmbedded**</p></th></tr></thead><tbody><tr><td><p>CMake</p></td><td><p>3.28.3</p></td><td><p>3.22.0</p></td><td><p>3.20.2</p></td><td><p>3.22.1</p></td><td><p>3.20.0</p></td><td><p>3.25.1</p></td><td><p>3.22.3</p></td></tr><tr><td><p>EmPY</p></td><td><p>3.3.4</p></td><td><p>3.3.2</p></td><td colspan="5"><p>3.3.4</p></td></tr><tr><td><p>Gazebo</p></td><td><p>Harmonic*</p></td><td><p>N/A</p></td><td><p>N/A</p></td><td><p>Harmonic*</p></td><td><p>Harmonic*</p></td><td><p>Harmonic*</p></td><td><p>N/A</p></td></tr><tr><td><p>NumPy</p></td><td><p>1.26.4</p></td><td><p>1.18.4</p></td><td><p>1.20.1</p></td><td><p>1.21.5</p></td><td><p>1.18.4</p></td><td><p>1.24.2</p></td><td><p>N/A</p></td></tr><tr><td><p>Ogre</p></td><td colspan="6"><p>1.12.10</p></td><td><p>N/A</p></td></tr><tr><td><p>OpenCV</p></td><td><p>4.6.0</p></td><td><p>3.4.6*</p></td><td><p>4.6.0</p></td><td><p>4.5.4</p></td><td><p>4.2.0</p></td><td><p>4.6.0</p></td><td><p>4.1.0 / 3.2.0***</p></td></tr><tr><td><p>OpenSSL</p></td><td><p>3.0.13</p></td><td><p>1.1.1l</p></td><td><p>3.0.7</p></td><td><p>1.1.1l</p></td><td><p>1.1.1f</p></td><td><p>3.0.11</p></td><td><p>1.1.1d / 1.1.1b***</p></td></tr><tr><td><p>Python</p></td><td><p>3.12.3</p></td><td><p>3.8.3</p></td><td><p>3.9.16</p></td><td><p>3.10.4</p></td><td><p>3.10.8</p></td><td><p>3.11.2</p></td><td><p>3.8.2 / 3.7.5***</p></td></tr><tr><td><p>Qt</p></td><td><p>5.15.10</p></td><td><p>5.12.12</p></td><td><p>5.15.3</p></td><td><p>5.15.3</p></td><td><p>5.12.3</p></td><td><p>5.15.8</p></td><td><p>5.14.1 / 5.12.5***</p></td></tr><tr><td colspan="2"></td><td colspan="6"><p><strong>Linux only</strong></p></td></tr><tr><td><p>PCL</p></td><td><p>1.14.0</p></td><td><p>N/A</p></td><td><p>1.12.0</p></td><td><p>1.12.1</p></td><td><p>N/A</p></td><td><p>1.13.0</p></td><td><p>1.10.0</p></td></tr><tr><td colspan="8"><p><strong>RMW DDS Middleware</strong></p></td></tr><tr><td><p>Cyclone DDS</p></td><td colspan="7"><p>0.10.4</p></td></tr><tr><td><p>Fast-DDS</p></td><td colspan="7"><p>2.14.0</p></td></tr><tr><td><p>Connext DDS</p></td><td colspan="5"><p>6.0.1</p></td><td colspan="2"><p>N/A</p></td></tr><tr><td><p>Gurum DDS</p></td><td colspan="2"><p>4.2.0</p></td><td colspan="5"><p>N/A</p></td></tr></tbody></table>

" \* " means that this is not the upstream version (available on the official Operating System repositories) but a package distributed by OSRF or the community (package built and distributed on custom repositories).

" \*\* " means that the dependency may see multiple version changes, because the dependency uses a package manager that continually updates the dependency without a stable API.

" \*\*\* " webOS OSE provides this different version.

This document only captures the version at the first release of a ROS distribution and will not be updated as the dependencies move forward. These versions are thus a low watermark.

Package manager use for dependencies:

- Ubuntu, Debian: apt, pip
- Windows: Chocolatey, pip
- macOS: Homebrew, pip
- RHEL: dnf
- OpenEmbedded: opkg

Build System Support:

- ament\_cmake
- cmake
- setuptools

## Changes to how ROS 2 and Gazebo integrate

Starting with Jazzy Jalisco, we are streamlining how ROS 2 and [Gazebo](https://gazebosim.org/) integrate. For every ROS 2 release, there will be a recommended, supported Gazebo release that goes along with that release. For Jazzy Jalisco, the recommended Gazebo release will be Harmonic.

To make it easier for ROS 2 packages to consume Gazebo packages, there are now `gz_*_vendor` packages. Those packages are:

- gz\_common\_vendor: [https://github.com/gazebo-release/gz\_common\_vendor](https://github.com/gazebo-release/gz_common_vendor)
- gz\_cmake\_vendor: [https://github.com/gazebo-release/gz\_cmake\_vendor](https://github.com/gazebo-release/gz_cmake_vendor)
- gz\_math\_vendor: [https://github.com/gazebo-release/gz\_math\_vendor](https://github.com/gazebo-release/gz_math_vendor)
- gz\_transport\_vendor: [https://github.com/gazebo-release/gz\_transport\_vendor](https://github.com/gazebo-release/gz_transport_vendor)
- gz\_sensor\_vendor: [https://github.com/gazebo-release/gz\_sensor\_vendor](https://github.com/gazebo-release/gz_sensor_vendor)
- gz\_sim\_vendor: [https://github.com/gazebo-release/gz\_sim\_vendor](https://github.com/gazebo-release/gz_sim_vendor)
- gz\_tools\_vendor: [https://github.com/gazebo-release/gz\_tools\_vendor](https://github.com/gazebo-release/gz_tools_vendor)
- gz\_utils\_vendor: [https://github.com/gazebo-release/gz\_utils\_vendor](https://github.com/gazebo-release/gz_utils_vendor)
- sdformat\_vendor: [https://github.com/gazebo-release/sdformat\_vendor](https://github.com/gazebo-release/sdformat_vendor)

ROS 2 packages can use the functionality in these packages by adding dependencies in `package.xml`, e.g.:

```
<depend>gz_math_vendor</depend>
```

And then using them in `CMakeLists.txt`, e.g.:

```
find_package(gz_math_vendor REQUIRED)
find_package(gz-math)

add_executable(my_executable src/exe.cpp)
target_link_libraries(my_executable gz-math::core)
```

> [!note] Note
> It will still be possible to use alternate Gazebo versions with Jazzy Jalisco. But those will not be as well tested or integrated with ROS 2. See [https://gazebosim.org/docs/harmonic/ros\_installation](https://gazebosim.org/docs/harmonic/ros_installation) for more information.

## New features in this ROS 2 release

### common\_interfaces

#### New VelocityStamped message

Added a new message with all fields needed to define a velocity and transform it.

See [https://github.com/ros2/common\_interfaces/pull/240](https://github.com/ros2/common_interfaces/pull/240) for more details.

#### Adds ARROW\_STRIP to Marker.msg

Added new type of Marker, `ARROW_STRIP`, to Marker.msg.

See [https://github.com/ros2/common\_interfaces/pull/242](https://github.com/ros2/common_interfaces/pull/242) for more details.

### image\_transport

#### Expose option to set callback groups

See [https://github.com/ros-perception/image\_common/issues/274](https://github.com/ros-perception/image_common/issues/274) for more details.

#### Enable allow list

Added parameter so users can selectively disable `image_transport` plugins at runtime.

See [https://github.com/ros-perception/image\_common/issues/264](https://github.com/ros-perception/image_common/issues/264) for more details.

#### Added rclcpp component to Republish

Users can now start the `image_transport` republisher node as an rclcpp\_component.

See [https://github.com/ros-perception/image\_common/issues/275](https://github.com/ros-perception/image_common/issues/275) for more details.

### message\_filters

#### TypeAdapters support

Allows users to use Type Adaptation within message\_filters.

See [https://github.com/ros2/message\_filters/pull/96](https://github.com/ros2/message_filters/pull/96) for more information.

### rcl

#### Add get type description service

Implements the `~/get_type_description` service which allows external users to get descriptions of each type that a node offers. This is offered by each node according to [REP 2016](https://github.com/ros-infrastructure/rep/pull/381).

See [https://github.com/ros2/rcl/pull/1052](https://github.com/ros2/rcl/pull/1052) for more details.

### rclcpp

#### Type support helper for services

New type support helper for services `rclcpp::get_service_typesupport_handle` is added to extract service type support handle.

See [https://github.com/ros2/rclcpp/pull/2209](https://github.com/ros2/rclcpp/pull/2209) for more details.

### rclpy

#### ParameterEventHandler

New class `ParameterEventHandler` allows us to monitor and respond changes to parameters via parameter events.

See [https://github.com/ros2/rclpy/pull/1135](https://github.com/ros2/rclpy/pull/1135) for more details.

### ros2cli

#### Added a --log-file-name command line argument

It is now possible to use `--log-file-name` command line argument to specify the log file name prefix.

```
$ ros2 run demo_nodes_cpp talker --ros-args --log-file-name filename
```

See [https://github.com/ros2/ros2cli/issues/856](https://github.com/ros2/ros2cli/issues/856) for more information.

#### Add clients and services count

It is now possible to get the number of clients created by a service.

### ros2action

#### type sub-command supported

It is now possible to use the `type` sub-command to check the action type.

```
$ ros2 action type /fibonacci
action_tutorials_interfaces/action/Fibonacci
```

See [https://github.com/ros2/ros2cli/pull/894](https://github.com/ros2/ros2cli/pull/894) for more information.

### rosbag2

#### Service recording and playback

It is now possible to record and play service data with the `ros2bag` command line interface.

This features builds on [Service Introspection](https://github.com/ros2/ros2/issues/1285), which has been available since Iron Irwini. [Service recording and display](https://github.com/ros2/rosbag2/pull/1480) adds the ability to record service data into a bag file. And [Service playback](https://github.com/ros2/rosbag2/pull/1481) can play that service data from the bag file.

Record all services data:

```
$ ros2 bag record --all-services
```

Record all services and all topic data:

```
$ ros2 bag record --all
```

Play service data from bag file:

```
$ ros2 bag play --publish-service-requests bag_path
```

See the [design document](https://github.com/ros2/rosbag2/blob/rolling/docs/design/rosbag2_record_replay_service.md) for more information.

#### New filter modes

It is now possible to filter by topic type.

```
$ ros2 bag record --topic_types sensor_msgs/msg/Image sensor_msgs/msg/CameraInfo
```

```
$ ros2 bag record --topic_types sensor_msgs/msg/Image
```

See more details [https://github.com/ros2/rosbag2/pull/1577](https://github.com/ros2/rosbag2/pull/1577) and [https://github.com/ros2/rosbag2/pull/1582](https://github.com/ros2/rosbag2/pull/1582).

#### Player and Recorder are now exposed as rclcpp components

This allows a “zero-copy” when using intra-process communication during data record or reply. This can significantly reduce CPU load during recording or reply when dealing with high-bandwidth data streams and will help to avoid data loss in the transport layer. It also provides the ability to use YAML configuration files for `rosbag2_transport::Player` and `rosbag2_transport::Recorder` composable nodes.

See [https://github.com/ros2/rosbag2/tree/jazzy?tab=readme-ov-file#using-with-composition](https://github.com/ros2/rosbag2/tree/jazzy?tab=readme-ov-file#using-with-composition) for more details.

#### Added option to disable recorder keyboard controls

See [https://github.com/ros2/rosbag2/pull/1607](https://github.com/ros2/rosbag2/pull/1607) for more details.

#### Added compression threads priority to record options

It is now possible to specify the priority of the thread that performs compression.

See [https://github.com/ros2/rosbag2/pull/1457](https://github.com/ros2/rosbag2/pull/1457) for more details.

#### Added ability to split already existing ros2 bags by time

Added `start_time_ns` and `end_time_ns` to the `StorageOptions` to exclude messages not in `[start_time;end_time]` during the `ros2 bag convert` operation.

See [https://github.com/ros2/rosbag2/pull/1455](https://github.com/ros2/rosbag2/pull/1455) for more details.

#### Added introspection QoS methods to Python bindings

It is now possible to instrospect QoS setting from Python bindings.

See [https://github.com/ros2/rosbag2/pull/1648](https://github.com/ros2/rosbag2/pull/1648) for more details.

### rosidl

#### Added interfaces to support key annotation

The `key` annotation allows indicating that a data member is part of the key, which can have zero or more key fields and can be applied to structure fields of various types.

See [https://github.com/ros2/rosidl/pull/796](https://github.com/ros2/rosidl/pull/796) and [https://github.com/ros2/rosidl\_typesupport\_fastrtps/pull/116](https://github.com/ros2/rosidl_typesupport_fastrtps/pull/116) for more details.

### rviz2

#### Added regex filter field for TF display

When there are many frames on `/tf` it can be hard to properly visualize them in RViz, especially if frames overlap. The usual solution to this is to enable and disable desired frames in Frames field of the TF display. Now it is possible to filter frames using regular expressions.

See [https://github.com/ros2/rviz/pull/1032](https://github.com/ros2/rviz/pull/1032) for more details.

#### Reset functionality

It is possible to reset Time using a new service or using the keyboard shortcut `R`.

See [https://github.com/ros2/rviz/issues/1109](https://github.com/ros2/rviz/issues/1109) and [https://github.com/ros2/rviz/issues/1088](https://github.com/ros2/rviz/issues/1088) for more details.

#### Added support for point\_cloud\_transport

It is possible to subscribe to point clouds using the `point_cloud_transport` package.

See [https://github.com/ros2/rviz/pull/1008](https://github.com/ros2/rviz/pull/1008) for more details.

#### Feature parity with RViz for ROS

It is possible to use the same plugins available in the ROS 1 version.

- DepthCloud
- AccelStamped
- TwistStamped
- WrenchStamped
- Effort

#### Camera info display

It is possible to visualize CameraInfo messages in the 3D scene.

See [https://github.com/ros2/rviz/pull/1166](https://github.com/ros2/rviz/pull/1166) for more details.

### rcpputils

#### Added tl\_expected

[std::expected](https://en.cppreference.com/w/cpp/utility/expected) is C++23 feature, which is not yet supported in ROS 2. However, it is possible to use `tl::expected` from rcpputils via a backported implementation.

See [https://github.com/ros2/rcpputils/pull/185](https://github.com/ros2/rcpputils/pull/185) for more details.

### rcutils

#### Add human readable date to logging formats

It is now possible to output dates in a human readable format when using console logging by using the `{date_time_with_ms}` token in the `RCUTILS_CONSOLE_OUTPUT_FORMAT` environment variable.

See [https://github.com/ros2/rcutils/pull/441](https://github.com/ros2/rcutils/pull/441) for more details.

## Changes since the Iron release

### common\_interfaces

#### Added IDs to geometry\_msgs/Polygon and PolygonStamped

Polygons are often used to represent specific objects but are difficult to rectify currently without any kind of specific identification. This feature adds an ID field to disambiguate polygons.

See [https://github.com/ros2/common\_interfaces/pull/232](https://github.com/ros2/common_interfaces/pull/232) for more details.

### geometry2

#### Removed deprecated headers

In Humble, the headers: `tf2_bullet/tf2_bullet.h`, `tf2_eigen/tf2_eigen.h`, `tf2_geometry_msgs/tf2_geometry_msgs.h`, `tf2_kdl/tf2_kdl.h`, `tf2_sensor_msgs/tf2_sensor_msgs.h` were deprecated in favor of: `tf2_bullet/tf2_bullet.hpp`, `tf2_eigen/tf2_eigen.hpp`, `tf2_geometry_msgs/tf2_geometry_msgs.hpp`, `tf2_kdl/tf2_kdl.hpp`, `tf2_sensor_msgs/tf2_sensor_msgs.hpp` In Jazzy, the `tf2_bullet/tf2_bullet.h`, `tf2_eigen/tf2_eigen.h`, `tf2_geometry_msgs/tf2_geometry_msgs.h`, `tf2_kdl/tf2_kdl.h`, `tf2_sensor_msgs/tf2_sensor_msgs.h` headers have been completely removed.

#### Changed return types of wait\_for\_transform\_async and wait\_for\_transform\_full\_async

Previously `wait_for_transform_async` and `wait_for_transform_full_async` of the `Buffer` class returned a future containing true or false In Jazzy, the future will contain the information of the transform being waited on.

#### Enabled Twist interpolator

Included new API to lookup the velocity of the moving frame in the reference frame.

See [https://github.com/ros2/geometry2/pull/646](https://github.com/ros2/geometry2/pull/646) for more information.

### rcl

#### Actual and expected call time when timer is called

New timer API `rcl_timer_call_with_info` is added to collect actual and expected call time when the timer is called. This allows users to get the timer information when the timer is expected to be called and actual time that timer is called.

See [https://github.com/ros2/rcl/pull/1113](https://github.com/ros2/rcl/pull/1113) for more details.

#### Improved rcl\_wait in the area of timeout computation and spurious wakeups

Added special handling for timers with a clock that has time override enabled. For these timer we should not compute a timeout, as the waitset is woken up by the associated guard condition.

See [https://github.com/ros2/rcl/issues/1146](https://github.com/ros2/rcl/issues/1146) for more details.

### rclcpp\_action

#### Callback after cancel

Added a function to stop callbacks of a goal handle after it has gone out of scope. This function allows us to drop the handle in a locked context.

See [https://github.com/ros2/rclcpp/pull/2281](https://github.com/ros2/rclcpp/pull/2281) for more details.

### rclcpp\_lifecycle

#### Add new node interface TypeDescriptionsInterface

Add new node interface `TypeDescriptionsInterface` to provide the `GetTypeDescription` service.

See [https://github.com/ros2/rclcpp/pull/2224](https://github.com/ros2/rclcpp/pull/2224) for more details.

### rclpy

#### rclpy.node.Node.declare\_parameter

The `rclpy.node.Node.declare_parameter` does not allow statically typing parameter without a default value.

See [https://github.com/ros2/rclpy/pull/1216](https://github.com/ros2/rclpy/pull/1216) for more details.

#### Added types to method arguments

Added type checking to improve the experience for anyone using static type checking.

See [https://github.com/ros2/rclcpp/pull/2224](https://github.com/ros2/rclcpp/pull/2224), [https://github.com/ros2/rclpy/issues/1240](https://github.com/ros2/rclpy/issues/1240), [https://github.com/ros2/rclpy/issues/1237](https://github.com/ros2/rclpy/issues/1237), [https://github.com/ros2/rclpy/issues/1231](https://github.com/ros2/rclpy/issues/1231), [https://github.com/ros2/rclpy/issues/1241](https://github.com/ros2/rclpy/issues/1241), and [https://github.com/ros2/rclpy/issues/1233](https://github.com/ros2/rclpy/issues/1233).

### rosbag2

#### Rename of the --exclude CLI option

The `--exclude` CLI option was renamed to the `--exclude-regex` to better reflect what it does.

See [https://github.com/ros2/rosbag2/pull/1480](https://github.com/ros2/rosbag2/pull/1480) for more information.

#### Added BagSplitInfo service call on bag close

See [https://github.com/ros2/rosbag2/pull/1422](https://github.com/ros2/rosbag2/pull/1422) for more details.

#### Added Python bindings for CompressionOptions and CompressionMode structures

See [https://github.com/ros2/rosbag2/pull/1425](https://github.com/ros2/rosbag2/pull/1425) for more details.

#### Improve performance in SqliteStorage::get\_bagfile\_size()

This minimizes the probability of losing messages during bag split operation when recording with the SQLite3 storage plugin.

See [https://github.com/ros2/rosbag2/pull/1516](https://github.com/ros2/rosbag2/pull/1516) for more details.

### rqt\_bag

#### Improved performance and updated rosbag API

There are some breaking changes in the rosbag2 API and Ubuntu Noble library versions that required some changes to `rqt_bag`.

See [https://github.com/ros-visualization/rqt\_bag/pull/156](https://github.com/ros-visualization/rqt_bag/pull/156) for more details.

## Development progress

For progress on the development of Jazzy Jalisco, see [this project board](https://github.com/orgs/ros2/projects/52).

For the broad process followed by Jazzy Jalisco, see the [process description page](https://docs.ros.org/en/jazzy/Releases/Release-Process.html).

## Known Issues

To come.

## Release Timeline

[^1]: Preliminary testing and stabilization of ROS Base packages, and API and feature freeze for RMW provider packages.

[^2]: API and feature freeze for ROS Base packages in Rolling Ridley. Only bug fix releases should be made after this point. New packages can be released independently.

[^3]: Branch from Rolling Ridley. `rosdistro` is reopened for Rolling PRs for ROS Base packages. Jazzy development shifts from `ros-rolling-*` packages to `ros-jazzy-*` packages.

[^4]: Updated releases of ROS Desktop packages available. Call for general testing.

[^5]: Release Candidate packages are built. Updated releases of ROS Desktop packages available.