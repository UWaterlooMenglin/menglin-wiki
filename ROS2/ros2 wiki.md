# ROS 2 Wiki

This is the central entry point for ROS 2 documentation. All resources are linked directly from the raw clippings.

## Quick Start
Getting up and running with ROS 2 Jazzy.

#### Setup Sequence
- [[Ubuntu (deb packages) — ROS 2 Documentation Jazzy  documentation|Ubuntu Installation]]
- [[Configuring environment — ROS 2 Documentation Jazzy  documentation|Configuring Environment]]
- [[Creating a workspace — ROS 2 Documentation Jazzy  documentation|Creating a Workspace]]
- [[Creating a package — ROS 2 Documentation Jazzy  documentation|Creating a Package]]
- [[Using colcon to build packages — ROS 2 Documentation Jazzy  documentation|Using Colcon Build]]

#### Frequently Used Command Lines

| Category | Command | Description |
| :--- | :--- | :--- |
| **Environment** | `source /opt/ros/jazzy/setup.bash` | Source main ROS 2 installation |
| **Build** | `colcon build` | Build packages in current workspace |
| **Local Env** | `source install/setup.bash` | Source the local workspace after build |
| **Nodes** | `ros2 run <pkg> <exec>` | Run a specific node |
| **Nodes** | `ros2 node list` | List all active nodes |
| **Nodes** | `ros2 node info /<name>` | View detailed info for a specific node |
| **Topics** | `ros2 topic list` | List all active topics |
| **Topics** | `ros2 topic echo /<name>` | Print data streaming on a topic in real-time |
| **Topics** | `ros2 topic pub /<name> <type> '<data>'` | Manually publish data to a topic |
| **Topics** | `ros2 topic hz /<name>` | Check the publishing rate of a topic |
| **Services** | `ros2 service list` | List all available services |
| **Services** | `ros2 service call /<name> <type> '<data>'` | Request a service |
| **Params** | `ros2 param list` | List parameters for all nodes |
| **Params** | `ros2 param get /<node> <param>` | Get a specific parameter value |

**Brief Demo: Testing a Topic**
1. Run the talker: `ros2 run demo_nodes_cpp talker`
2. In a new terminal, verify the topic exists: `ros2 topic list`
3. Listen to the talker: `ros2 topic echo /chatter`

## Terminology & Concepts
These notes explain the "What" and "How" of ROS 2.

- [[Understanding nodes — ROS 2 Documentation Jazzy  documentation|Understanding Nodes]]
- [[Understanding topics — ROS 2 Documentation Jazzy  documentation|Understanding Topics]]
- [[Understanding services — ROS 2 Documentation Jazzy  documentation|Understanding Services]]
- [[Understanding actions — ROS 2 Documentation Jazzy  documentation|Understanding Actions]]
- [[Understanding parameters — ROS 2 Documentation Jazzy  documentation|Understanding Parameters]]

## Implementation & Demos
Practical application of core concepts.

- [[Launching nodes — ROS 2 Documentation Jazzy  documentation|Launching Nodes]]
- [[Writing a simple publisher and subscriber (Python) — ROS 2 Documentation Jazzy  documentation|Pub/Sub Demo]]
- [[Writing a simple service and client (Python) — ROS 2 Documentation Jazzy  documentation|Service/Client Demo]]

## Tools & Debugging
- [[Using turtlesim, ros2, and rqt — ROS 2 Documentation Jazzy  documentation|Turtlesim, ros2, and rqt]]
- [[Recording and playing back data — ROS 2 Documentation Jazzy  documentation|Recording & Playback]]
- [[Using rqt_console to view logs — ROS 2 Documentation Jazzy  documentation|rqt_console Logs]]

## General Info
- [[ROS 2 Documentation — ROS 2 Documentation Jazzy  documentation|ROS 2 Documentation Home]]
- [[Jazzy Jalisco (jazzy) — ROS 2 Documentation Jazzy  documentation|Jazzy Jalisco Overview]]
- [[Distributions — ROS 2 Documentation Jazzy  documentation|ROS 2 Distributions]]

---
*Note: This wiki links directly to files in `/raw/ROS2`.*
