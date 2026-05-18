# ROS 2 Wiki

## What is ROS 2?

**ROS (Robot Operating System) 2** is an open-source ecosystem providing a framework, tools, and libraries for building, deploying, running, and maintaining robotic applications. It's the "plumbing" that enables communication between different parts of a robot.

### Key Characteristics
- **Middleware framework**: Provides messaging and communication infrastructure
- **Multi-language support**: Works with C++, Python, and other languages
- **Cross-platform**: Available on Ubuntu, Windows, macOS, and other platforms
- **Modular architecture**: Built on nodes, topics, services, and actions

### Why ROS 2?
- Industry standard for robotics development
- Strong community and ecosystem
- Decoupled system design encourages modularity
- Built-in tools for introspection, debugging, and simulation

---

## Quick Start

Get ROS 2 running in 5 minutes with the demo nodes:

### 1. Install ROS 2 (Ubuntu - Recommended)
```bash
# For Desktop (Recommended):
sudo apt install ros-kilted-desktop

# OR for ROS-Base (minimal):
sudo apt install ros-kilted-ros-base
```

### 2. Source the setup file
```bash
source /opt/ros/kilted/setup.bash
```

### 3. Verify Installation - Run the demo
**Terminal 1** - Run the talker (publisher):
```bash
ros2 run demo_nodes_cpp talker
```

**Terminal 2** - Run the listener (subscriber):
```bash
ros2 run demo_nodes_py listener
```

**Expected output:** Talker publishes messages → Listener receives them ✓

### Next Steps
- Explore [[#Installation]] for other platforms
- Try [[#Popular Commands]] to interact with ROS 2
- Follow the [[#ROS Learning Path]] for structured learning

---

## Installation

### Ubuntu - Desktop (Recommended for Beginners)

**Setup locale:**
```bash
locale  # check for UTF-8
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
locale  # verify
```

**Enable repositories:**
```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F'"' '{print $4}')
curl -L -o /tmp/ros2-apt-source.deb "https://github.com/ros-infrastructure/ros-apt-source/releases/download/${ROS_APT_SOURCE_VERSION}/ros2-apt-source_${ROS_APT_SOURCE_VERSION}.$(. /etc/os-release && echo ${UBUNTU_CODENAME:-${VERSION_CODENAME}})_all.deb"
sudo dpkg -i /tmp/ros2-apt-source.deb
```

**Install ROS 2:**
```bash
sudo apt update
sudo apt upgrade
sudo apt install ros-kilted-desktop  # Desktop (recommended)
```

**Setup environment:**
```bash
source /opt/ros/kilted/setup.bash
```

---

### Ubuntu - Binary (Pre-built)

Download from [ROS 2 releases page](https://github.com/ros2/ros2/releases) and extract:
```bash
mkdir -p ~/ros2_kilted
cd ~/ros2_kilted
tar xf ~/Downloads/ros2-package-linux-x86_64.tar.bz2
. ~/ros2_kilted/ros2-linux/setup.bash
```

---

### Ubuntu - Source (Development)

For advanced users who want to build from source:

**Install build tools:**
```bash
sudo apt update && sudo apt install -y \
  python3-mypy \
  python3-pip \
  python3-pytest \
  python3-pytest-cov \
  python3-pytest-mock \
  python3-pytest-repeat \
  python3-pytest-rerunfailures \
  python3-pytest-runner \
  python3-pytest-timeout \
  ros-dev-tools
```

**Clone and build:**
```bash
mkdir -p ~/ros2_kilted/src
cd ~/ros2_kilted
vcs import --input https://raw.githubusercontent.com/ros2/ros2/kilted/ros2.repos src
rosdep install --from-paths src --ignore-src -y --skip-keys "fastcdr rti-connext-dds-7.3.0 urdfdom_headers"
colcon build --symlink-install --mixin release
source ~/ros2_kilted/install/local_setup.bash
```

---

## Popular Commands

Quick reference guide organized by task. All commands assume you've sourced the setup file (`source /opt/ros/kilted/setup.bash`).

### Setup & Installation

| Command | Purpose | Example |
|---------|---------|---------|
| `source /opt/ros/kilted/setup.bash` | Activate ROS 2 environment | `source /opt/ros/kilted/setup.bash` |
| `printenv \| grep -i ROS` | Verify ROS 2 is sourced | `printenv \| grep -i ROS` |
| `sudo apt install ros-dev-tools` | Install development tools | `sudo apt install ros-dev-tools` |
| `rosdep init` | Initialize rosdep package manager | One-time setup: `sudo rosdep init && rosdep update` |

### Building & Packages

| Command | Purpose | Example |
|---------|---------|---------|
| `colcon build` | Build all packages in workspace | `cd ~/ros2_workspace && colcon build` |
| `colcon build --packages-select <pkg>` | Build specific package | `colcon build --packages-select my_robot_pkg` |
| `colcon build --symlink-install` | Link install (faster development) | `colcon build --symlink-install` |
| `ros2 pkg list` | List all available packages | `ros2 pkg list \| head` |
| `ros2 pkg prefix <pkg>` | Get package installation path | `ros2 pkg prefix demo_nodes_cpp` |

### Running & Communication

| Command | Purpose | Example |
|---------|---------|---------|
| `ros2 run <pkg> <node>` | Run a single node | `ros2 run demo_nodes_cpp talker` |
| `ros2 topic list` | List all active topics | `ros2 topic list` |
| `ros2 topic echo <topic>` | Print topic messages | `ros2 topic echo /turtle1/pose` |
| `ros2 topic pub <topic> <msg_type> <data>` | Publish message to topic | `ros2 topic pub /turtle1/cmd_vel geometry_msgs/Twist "{linear: {x: 1.0}}"` |
| `ros2 service list` | List all available services | `ros2 service list` |
| `ros2 service call <srv> <srv_type> <data>` | Call a service | `ros2 service call /spawn turtlesim/srv/Spawn "{x: 2, y: 2}"` |
| `ros2 param list` | List all parameters | `ros2 param list` |
| `ros2 param get <node> <param>` | Get parameter value | `ros2 param get /turtlesim set_pen_color` |
| `ros2 param set <node> <param> <value>` | Set parameter value | `ros2 param set /turtlesim background_g 255` |

### Debugging & Introspection

| Command | Purpose | Example |
|---------|---------|---------|
| `ros2 node list` | List all running nodes | `ros2 node list` |
| `ros2 node info <node>` | Get detailed node information | `ros2 node info /turtlesim` |
| `ros2 topic info <topic>` | Get topic statistics and subscribers | `ros2 topic info /turtle1/pose` |
| `rqt_console` | GUI log viewer | `rqt_console` (see node logs in real-time) |
| `ros2 bag record <topic>` | Record topic to bag file | `ros2 bag record /turtle1/pose` |
| `ros2 bag play <bag_file>` | Playback recorded bag | `ros2 bag play rosbag2_2024_05_18` |
| `ros2 doctor` | Diagnose ROS 2 setup issues | `ros2 doctor` |

### Testing & Maintenance

| Command | Purpose | Example |
|---------|---------|---------|
| `colcon test` | Run all tests in workspace | `colcon test --packages-select my_pkg` |
| `colcon test --packages-select <pkg>` | Test specific package | `colcon test --packages-select my_pkg` |
| `vcs import src < ros2.repos` | Import repositories from file | Update source installation: `vcs import src < ros2.repos` |
| `vcs pull src` | Update all repositories | `vcs pull src` (keep source code up-to-date) |
| `colcon build --symlink-install --mixin release` | Build in release mode | Optimized build: `colcon build --symlink-install --mixin release` |

### Turtlesim (Learning Tool)

| Command | Purpose | Example |
|---------|---------|---------|
| `ros2 run turtlesim turtlesim_node` | Start turtlesim simulator | `ros2 run turtlesim turtlesim_node` |
| `ros2 run turtlesim turtle_teleop_key` | Control turtle with keyboard | `ros2 run turtlesim turtle_teleop_key` |
| `ros2 run turtlesim draw_square` | Run example drawing node | `ros2 run turtlesim draw_square` |

---

## ROS Learning Path

A structured progression from beginner concepts to practical development. Based on the official [[First steps with ROS - learning path]].

### Phase 1: Core Concepts (Foundations)
Start with understanding how ROS 2 works:

1. **[[#What is ROS 2?]]** - What you're learning and why
2. **[[#Installation]]** - Get ROS 2 running on your system
3. **Understanding Nodes** - Individual programs/processes in ROS
4. **Understanding Topics** - Publisher/subscriber communication pattern
5. **Understanding Services** - Request/response communication pattern
6. **Understanding Parameters** - Configuration management
7. **Understanding Actions** - Goal-oriented communication with feedback

**Tools for this phase:**
- `turtlesim` - Visual 2D simulator for learning
- `rqt_console` - Log viewer for introspection
- `ros2` CLI tools (topic, service, param commands)

---

### Phase 2: Practical Development (Working with Code)

Once you understand core concepts, build actual packages:

1. **Creating a workspace** - Set up your development environment
2. **Creating packages** - Package your code and dependencies
3. **Writing publishers and subscribers** - Implement topic-based communication
   - C++ implementation
   - Python implementation
4. **Writing services** - Implement request/response patterns
   - C++ implementation
   - Python implementation
5. **Working with custom messages** - Define your own data types
6. **Using parameters** - Make your nodes configurable

**Tools for this phase:**
- `colcon` - Build system
- `ros2 pkg` - Package utilities
- Code editors/IDEs (VS Code, PyCharm, etc.)

---

### Phase 3: Advanced Topics (Beyond Basics)

Explore intermediate and advanced concepts:

- **Launch files** - Start multiple nodes with configuration
- **Recording and playback** (bag files) - Debug and share robot data
- **tf2** (transforms) - Handle coordinate frames for multi-body systems
- **URDF** - Describe robot structure and kinematics
- **RViz** - 3D visualization tool
- **Actions** - Complex task execution with feedback
- **Composable nodes** - Combine nodes in single process
- **Testing** - Write unit and integration tests
- **Security** - Authentication and encryption for distributed systems

---

## Learning Resources

### Official Documentation
- **ROS 2 Official Docs**: https://docs.ros.org/en/kilted/
- **Tutorials**: Follow the official tutorials in order; they build on each other
- **How-To Guides**: Quick solutions for specific questions

### Structured Learning
1. Complete the **First Steps** learning path (see [[#ROS Learning Path]])
2. Work through **Beginner: CLI Tools** tutorials
3. Progress to **Beginner: Client Libraries** (choose C++ or Python)
4. Move to **Intermediate** tutorials as you grow

### Getting Help
- **ROS Discourse**: https://discourse.ros.org/ (official community forum)
- **Stack Overflow**: Tag with `ros2` and `robotics`
- **GitHub Issues**: Report bugs in package repositories

### Key Learning Tools
- **turtlesim**: 2D simulator for learning basic concepts without hardware
- **rqt**: GUI tool collection for visualization and debugging
- **ros2doctor**: Diagnose ROS 2 installation issues

### Your Learning Notes (evolves as you progress)
- **[Beginner phase]** - Focus on understanding nodes, topics, services
- **[Intermediate phase]** - Build actual packages with real communication patterns
- **[Advanced phase]** - Add complexity: transforms, visualization, testing, hardware integration

---

## Core Concepts

A reference for fundamental ROS 2 concepts. This section expands as you learn deeper topics.

### Nodes
- Individual executables/programs in ROS 2
- Communicate through topics, services, or actions
- Can be written in C++, Python, or other languages
- Run independently and can be distributed across machines

### Topics
- **Publisher/Subscriber** pattern for continuous data flow
- One-way communication (publisher → subscribers)
- Asynchronous - subscribers don't block publishers
- Use case: sensor data (camera, lidar, odometry)

### Services
- **Request/Response** pattern for specific tasks
- Synchronous - requester waits for response
- One-to-one communication (client → server)
- Use case: spawning entities, setting configurations, commanding actions

### Parameters
- Configuration values for nodes
- Can be set at runtime without restarting
- Hierarchically organized with namespaces
- Use case: tuning controller gains, setting speeds, enabling/disabling features

### Actions
- **Goal/Result/Feedback** pattern for long-running tasks
- Client sends goal → Server executes → Sends periodic feedback → Returns result
- Asynchronous with preemption support
- Use case: moving robot to waypoint, executing complex behaviors

---

## Troubleshooting

### ROS 2 not found after installation
```bash
# Make sure to source setup file in EVERY new terminal
source /opt/ros/kilted/setup.bash

# To make permanent, add to ~/.bashrc:
echo "source /opt/ros/kilted/setup.bash" >> ~/.bashrc
```

### "Unsupported OS" error on non-standard Ubuntu
```bash
# Append this to rosdep commands:
--os=ubuntu:noble
```

### Build failures with missing dependencies
```bash
# Update system packages
sudo apt upgrade

# Install missing dependencies
rosdep install --from-paths src --ignore-src -y

# For source installs, specify skip-keys if needed
rosdep install --from-paths src --ignore-src -y --skip-keys "fastcdr rti-connext-dds-7.3.0"
```

### Bag file access denied
```bash
# Make sure ros2.bag exists and check permissions:
ls -la ros2.bag
# If owned by root, use sudo or change owner:
sudo chown $USER:$USER ros2.bag
```

---

## Content Workflow (For Future Updates)

This section documents how to maintain and evolve this wiki.

### Intake Process
- New raw documentation comes from `@raw\ROS2\` folder
- Extract key information without modifying original files
- Synthesize content into appropriate wiki sections

### File Naming Convention
- Main wiki: `ROS2-wiki.md` (this file)
- Concept deep-dives: `ROS2-concepts-<topic>.md` (e.g., `ROS2-concepts-nodes.md`)
- Tutorials: `ROS2-tutorial-<task>.md` (e.g., `ROS2-tutorial-first-package.md`)
- Examples: `ROS2-example-<pattern>.md` (e.g., `ROS2-example-pub-sub.md`)

### Linking Strategy
- Link to specific sections with `[[filename#Heading]]`
- Group related concepts and link them together
- Create cross-wiki links as your knowledge base grows

### Evolution Markers
- **[Beginner]** - Topics suitable for first learning
- **[Intermediate]** - Build on beginner knowledge, require practice
- **[Advanced]** - Deep technical content, requires experience
- Remove markers as content becomes universal/foundational

### When to Create New Files
- If a section exceeds 500 lines
- If a concept deserves independent explanation
- If multiple pages need to link to it (e.g., detailed explanation of tf2)

### When to Expand Current File
- Adding examples to existing sections
- Updating command references
- Adding learning notes based on experience

---

**Last updated:** 2026-05-18  
**ROS Distribution:** Kilted Kaiju (2025)  
**Status:** Beginner-focused, will evolve as learning progresses
