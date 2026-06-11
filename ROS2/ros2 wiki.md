# ROS 2 Wiki

This is the central entry point for ROS 2 documentation. All resources are linked directly from the raw clippings.

## Quick Start
Getting up and running with ROS 2 Jazzy.

### Setup Sequence
- [[Ubuntu (deb packages) — ROS2-Jazzy|Ubuntu Installation]]
- [[Configuring environment — ROS2-Jazzy|Configuring Environment]]
- [[Creating a workspace — ROS2-Jazzy|Creating a Workspace]]
- [[Creating a package — ROS2-Jazzy|Creating a Package]]
- [[Using colcon to build packages — ROS2-Jazzy|Using Colcon Build]]
- [[Managing Dependencies with rosdep — ROS2-Jazzy|Dependency Management (rosdep)]]

### Frequently Used Command Lines

| Category | Command | Description | Linked Concept |
| :--- | :--- | :--- | :--- |
| **Environment** | `source /opt/ros/jazzy/setup.bash` | Source main ROS 2 installation | [[Configuring environment — ROS2-Jazzy\|Env Setup]] |
| **Build** | `colcon build` | Build packages in current workspace | [[Using colcon to build packages — ROS2-Jazzy\|Colcon]] |
| **Local Env** | `source install/setup.bash` | Source the local workspace after build | [[Creating a workspace — ROS2-Jazzy\|Workspace]] |
| **Nodes** | `ros2 run <pkg> <exec>` | Run a specific node | [[Understanding nodes — ROS2-Jazzy\|Nodes]] |
| **Nodes** | `ros2 node list` | List all active nodes | [[Understanding nodes — ROS2-Jazzy\|Nodes]] |
| **Nodes** | `ros2 node info /<name>` | View detailed info for a specific node | [[Understanding nodes — ROS2-Jazzy\|Nodes]] |
| **Topics** | `ros2 topic list` | List all active topics | [[Understanding topics — ROS2-Jazzy\|Topics]] |
| **Topics** | `ros2 topic echo /<name>` | Print data streaming in real-time | [[Understanding topics — ROS2-Jazzy\|Topics]] |
| **Topics** | `ros2 topic pub /<name> <type> '<data>'` | Manually publish data to a topic | [[Understanding topics — ROS2-Jazzy\|Topics]] |
| **Topics** | `ros2 topic hz /<name>` | Check the publishing rate of a topic | [[Understanding topics — ROS2-Jazzy\|Topics]] |
| **Topics** | `ros2 topic info /<name>` | View topic type and publishers/subscribers | [[Understanding topics — ROS2-Jazzy\|Topics]] |
| **Services** | `ros2 service list` | List all available services | [[Understanding services — ROS2-Jazzy\|Services]] |
| **Services** | `ros2 service call /<name> <type> '<data>'` | Request a service | [[Understanding services — ROS2-Jazzy\|Services]] |
| **Services** | `ros2 service type /<name>` | Get the service type | [[Understanding services — ROS2-Jazzy\|Services]] |
| **Params** | `ros2 param list` | List parameters for all nodes | [[Understanding parameters — ROS2-Jazzy\|Parameters]] |
| **Params** | `ros2 param get /<node> <param>` | Get a specific parameter value | [[Understanding parameters — ROS2-Jazzy\|Parameters]] |
| **Params** | `ros2 param set /<node> <param> <val>` | Set a parameter value | [[Understanding parameters — ROS2-Jazzy\|Parameters]] |
| **Actions** | `ros2 action list` | List all available actions | [[Understanding actions — ROS2-Jazzy\|Actions]] |
| **Actions** | `ros2 action send_goal /<name> <type> '<data>'` | Send a goal to an action server | [[Understanding actions — ROS2-Jazzy\|Actions]] |
| **Launch** | `ros2 launch <pkg> <launch_file> [args:=val]` | Launch a robot/system with specific models | [[Creating a launch file — ROS2-Jazzy\|Launch]] |
| **Model Desc** | `check_urdf <file.urdf>` | Verify URDF syntax and structure | [[Generating an URDF File — ROS2-Jazzy\|Generating URDF]] |
| **Model Desc** | `urdf_to_graph <file.urdf>` | Visualize URDF hierarchy | [[Generating an URDF File — ROS2-Jazzy\|Generating URDF]] |
| **Robot Model** | `ros2 run robot_state_publisher robot_state_publisher` | Publish URDF state to /robot_description | [[Using URDF with robot_state_publisher (Python) — ROS2-Jazzy\|URDF Publisher]] |
| **Robot Model** | `ros2 run joint_state_publisher_gui joint_state_publisher_gui` | GUI to test joint movements | [[Building a movable robot model — ROS2-Jazzy\|Movable Model]] |
| **Sim/Viz** | `rviz2` | Launch 3D visualization shell | [[Using turtlesim, ros2, and rqt — ROS2-Jazzy\|Viz Tools]] |
| **Sim/Viz** | `gazebo` | Launch Gazebo simulator shell | [[Building a movable robot model — ROS2-Jazzy\|Sim]] |
| **Debug** | `rqt_graph` | Visualize the node communication graph | [[Understanding nodes — ROS2-Jazzy\|Graph]] |
| **Debug** | `rqt_console` | View aggregated logs from all nodes | [[Using rqt_console to view logs — ROS2-Jazzy\|Log View]] |
| **Debug** | `ros2 bag record /<topic>` | Record topic data for later analysis | [[Recording and playing back data — ROS2-Jazzy\|Bags]] |
| **Debug** | `ros2 bag play <bag_file>` | Replay recorded data into the system | [[Recording and playing back data — ROS2-Jazzy\|Bags]] |

**Brief Demo: Testing a Topic**
1. Run the talker: `ros2 run demo_nodes_cpp talker`
2. In a new terminal, verify the topic exists: `ros2 topic list`
3. Listen to the talker: `ros2 topic echo /chatter`

## Terminology & Concepts
These notes explain the "What" and "How" of ROS 2.

- [[Understanding nodes — ROS2-Jazzy|Understanding Nodes]]
- [[Understanding topics — ROS2-Jazzy|Understanding Topics]]
- [[Understanding services — ROS2-Jazzy|Understanding Services]]
- [[Understanding actions — ROS2-Jazzy|Understanding Actions]]
- [[Understanding parameters — ROS2-Jazzy|Understanding Parameters]]

## Implementation & Demos
Practical application of core concepts.

- [[Launching nodes — ROS2-Jazzy|Launching Nodes]]
- [[Writing a simple publisher and subscriber (Python) — ROS2-Jazzy|Pub/Sub Demo]]
- [[Writing a simple service and client (Python) — ROS2-Jazzy|Service/Client Demo]]
- [[Creating an action — ROS2-Jazzy|Creating an Action]]
- [[Writing an action server and client (Python) — ROS2-Jazzy|Action Implementation Demo]]
- [[Using parameters in a class (Python) — ROS2-Jazzy|Parameters Implementation Demo]]
- [[Creating a launch file — ROS2-Jazzy|Creating Launch Files]]
- [[Integrating launch files into ROS 2 packages — ROS2-Jazzy|Integrating Launch Files]]

## Robot Modeling (URDF & Onshape)
Specialized workflow for robot description and modeling.

- [[Getting started — Onshape to robot|Onshape to Robot: Getting Started]]
- [[Design-time considerations — Onshape to robot|Onshape: Design Considerations]]
- [[Configuration (config.json) — Onshape to robot|Onshape: Configuration]]
- [[Generating an URDF File — ROS2-Jazzy|Generating URDF]]
- [[Building a visual robot model from scratch — ROS2-Jazzy|Visual Robot Model]]
- [[Adding physical and collision properties — ROS2-Jazzy|Physical & Collision Properties]]
- [[Building a movable robot model — ROS2-Jazzy|Movable Robot Model]]
- [[Using URDF with robot_state_publisher (Python) — ROS2-Jazzy|Using URDF with robot_state_publisher]]

## Tools & Debugging
- [[Using turtlesim, ros2, and rqt — ROS2-Jazzy|Turtlesim, ros2, and rqt]]
- [[Recording and playing back data — ROS2-Jazzy|Recording & Playback]]
- [[Using rqt_console to view logs — ROS2-Jazzy|rqt_console Logs]]

## General Info
- [[ROS 2 Documentation — ROS2-Jazzy|ROS 2 Documentation Home]]
- [[Jazzy Jalisco (jazzy) — ROS2-Jazzy|Jazzy Jalisco Overview]]
- [[Distributions — ROS2-Jazzy|ROS 2 Distributions]]

---
*Note: This wiki links directly to files in `/raw/ROS2`.*
