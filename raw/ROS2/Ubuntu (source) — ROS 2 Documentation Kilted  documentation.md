---
title: "Ubuntu (source) — ROS 2 Documentation: Kilted  documentation"
source: "https://docs.ros.org/en/kilted/Installation/Alternatives/Ubuntu-Development-Setup.html"
author:
published:
created: 2026-05-18
description:
tags:
  - "clippings"
---
## Ubuntu (source)

## System requirements

The current Debian-based target platforms for Kilted Kaiju are:

- Tier 1: Ubuntu Linux - Noble (24.04) 64-bit
- Tier 3: Debian Linux - Bookworm (12) 64-bit

As defined in [REP 2000](https://reps.openrobotics.org/rep-2000/).

## System setup

### Set locale

Make sure you have a locale which supports `UTF-8`. If you are in a minimal environment (such as a docker container), the locale may be something minimal like `POSIX`. We test with the following settings. However, it should be fine if you’re using a different UTF-8 supported locale.

```
$ locale  # check for UTF-8

$ sudo apt update && sudo apt install locales
$ sudo locale-gen en_US en_US.UTF-8
$ sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
$ export LANG=en_US.UTF-8

$ locale  # verify settings
```

### Enable required repositories

You will need to add the ROS 2 apt repository to your system.

First ensure that the [Ubuntu Universe repository](https://help.ubuntu.com/community/Repositories/Ubuntu) is enabled.

```
$ sudo apt install software-properties-common
$ sudo add-apt-repository universe
```

The [ros-apt-source](https://github.com/ros-infrastructure/ros-apt-source/) packages provide keys and apt source configuration for the various ROS repositories.

Installing the ros2-apt-source package will configure ROS 2 repositories for your system. Updates to repository configuration will occur automatically when new versions of this package are released to the ROS repositories.

```
$ sudo apt update && sudo apt install curl -y
$ export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F'"' '{print $4}')
$ curl -L -o /tmp/ros2-apt-source.deb "https://github.com/ros-infrastructure/ros-apt-source/releases/download/${ROS_APT_SOURCE_VERSION}/ros2-apt-source_${ROS_APT_SOURCE_VERSION}.$(. /etc/os-release && echo ${UBUNTU_CODENAME:-${VERSION_CODENAME}})_all.deb"
$ sudo dpkg -i /tmp/ros2-apt-source.deb
```

### Install development tools

```
$ sudo apt update && sudo apt install -y \
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

## Build ROS 2

### Get ROS 2 code

Create a workspace and clone all repos:

```
$ mkdir -p ~/ros2_kilted/src
$ cd ~/ros2_kilted
$ vcs import --input https://raw.githubusercontent.com/ros2/ros2/kilted/ros2.repos src
```

### Install dependencies using rosdep

ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.

```
$ sudo apt upgrade
```

```
$ sudo rosdep init
$ rosdep update
$ rosdep install --from-paths src --ignore-src -y --skip-keys "fastcdr rti-connext-dds-7.3.0 urdfdom_headers"
```

**Note**: If you’re using a distribution that is based on Ubuntu (like Linux Mint) but does not identify itself as such, you’ll get an error message like `Unsupported OS [mint]`. In this case append `--os=ubuntu:noble` to the above command.

### Install additional RMW implementations (optional)

The default middleware that ROS 2 uses is `Fast DDS`, but the middleware (RMW) can be replaced at build or runtime. See the [guide](https://docs.ros.org/en/kilted/How-To-Guides/Working-with-multiple-RMW-implementations.html) on how to work with multiple RMWs.

### Install colcon mixins

```
$ colcon mixin add default https://github.com/colcon/colcon-defaults/raw/master/index.yaml
$ colcon mixin update default
```

### Build the code in the workspace

If you have already installed ROS 2 another way (either via debs or the binary distribution), make sure that you run the below commands in a fresh environment that does not have those other installations sourced. Also ensure that you do not have `source /opt/ros/${ROS_DISTRO}/setup.bash` in your `.bashrc`. You can make sure that ROS 2 is not sourced with the command `printenv | grep -i ROS`. The output should be empty.

More info on working with a ROS workspace can be found in [this tutorial](https://docs.ros.org/en/kilted/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html).

```
$ cd ~/ros2_kilted/
$ colcon build --symlink-install --mixin release
```

> [!note] Note
> If you are having trouble compiling all examples and this is preventing you from completing a successful build, you can use the `--packages-skip` colcon flag to ignore the package that is causing problems. For instance, if you don’t want to install the large OpenCV library, you could skip building the packages that depend on it using the command:
> 
> ```
> $ colcon build --symlink-install --packages-skip image_tools intra_process_demo
> ```

## Setup environment

Set up your environment by sourcing the following file.

```
$ . ~/ros2_kilted/install/local_setup.bash
```

> [!note] Note
> Replace `.bash` with your shell if you’re not using bash. Possible values are: `setup.bash`, `setup.sh`, `setup.zsh`.

## Try some examples

In one terminal, source the setup file and then run a C++ `talker`:

```
$ . ~/ros2_kilted/install/local_setup.bash
$ ros2 run demo_nodes_cpp talker
```

In another terminal source the setup file and then run a Python `listener`:

```
$ . ~/ros2_kilted/install/local_setup.bash
$ ros2 run demo_nodes_py listener
```

You should see the `talker` saying that it’s `Publishing` messages and the `listener` saying `I heard` those messages. This verifies both the C++ and Python APIs are working properly. Hooray!

## Alternate compilers

Using a different compiler besides gcc to compile ROS 2 is easy. If you set the environment variables `CC` and `CXX` to executables for a working C and C++ compiler, respectively, and retrigger CMake configuration (by using `--cmake-force-configure` or by deleting the packages you want to be affected), CMake will reconfigure and use the different compiler.

### Clang

To configure CMake to detect and use Clang:

```
$ sudo apt install clang
$ export CC=clang
$ export CXX=clang++
$ colcon build --cmake-force-configure
```

## Stay up to date

See [Maintain source checkout](https://docs.ros.org/en/kilted/Installation/Maintaining-a-Source-Checkout.html) to periodically refresh your source installation.

## Troubleshoot

Troubleshooting techniques can be found [here](https://docs.ros.org/en/kilted/How-To-Guides/Installation-Troubleshooting.html#linux-troubleshooting).

## Uninstall

1. If you installed your workspace with colcon as instructed above, “uninstalling” could be just a matter of opening a new terminal and not sourcing the workspace’s `setup` file. This way, your environment will behave as though there is no Kilted install on your system.
2. If you’re also trying to free up space, you can delete the entire workspace directory with:
	```
	$ rm -rf ~/ros2_kilted
	```