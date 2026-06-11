---
title: "Generating an URDF File — ROS 2 Documentation: Jazzy  documentation"
source: "https://docs.ros.org/en/jazzy/Tutorials/Intermediate/URDF/Exporting-an-URDF-File.html"
author:
published:
created: 2026-06-11
description:
tags:
  - "clippings"
---
**You're reading the documentation for an older, but still supported, version of ROS 2. For information on the latest version, please have a look at [Lyrical](https://docs.ros.org/en/lyrical/Tutorials/Intermediate/URDF/Exporting-an-URDF-File.html).**

## Generating an URDF File

**Goal:** Learn how to Export an URDF File

**Tutorial level:** Intermediate

**Time:** 5 minutes

Most roboticists work in teams, and often those teams include a mechanical engineer who develops a CAD model of robot. Instead of crafting an URDF by hand it is possible to export an URDF model from many different CAD and modeling programs. These export tools are often developed by individuals that are familiar with the particular CAD program they use. Below you will find a list of available URDF exporters for a variety of CAD and 3D modeling software systems. *The ROS core maintainers do not maintain these packages. As such we make no claims about their performance or ease of use.* However, we figured it would be helpful to produce a list of available URDF exporters.

**CAD Exporters**

> - [Blender URDF Exporter](https://github.com/dfki-ric/phobos)
> - [CREO Parametric URDF Exporter](https://github.com/icub-tech-iit/creo2urdf)
> - [FreeCAD ROS Workbench](https://github.com/galou/freecad.cross)
> - [RobotCAD (FreeCAD OVERCROSS)](https://github.com/drfenixion/freecad.overcross)
> - [Freecad to Gazebo Exporter](https://github.com/Dave-Elec/freecad_to_gazebo)
> - [Fusion 360 URDF Exporter](https://github.com/dheena2k2/fusion2urdf-ros2)
> - [fusion2URDF (Fusion 360, ros2\_control, closed loops)](https://github.com/Adriaeik/fusion2URDF)
> - [FusionSDF: Fusion 360 to SDF exporter](https://github.com/andreasBihlmaier/FusionSDF)
> - [OnShape URDF Exporter](https://github.com/Rhoban/onshape-to-robot)
> - [SolidWorks URDF Exporter](https://github.com/ros/solidworks_urdf_exporter)
> - [ExportURDF Library (Fusion360, OnShape, Solidworks)](https://github.com/daviddorf2023/ExportURDF)

**Other URDF Export and Conversion Tools**

> - [Gazebo SDFormat to URDF Parser](https://github.com/ros/sdformat_urdf/tree/jazzy)
> - [SDF to URDF Converter in Python](https://github.com/andreasBihlmaier/pysdf)
> - [URDF to Webots Simulator Format](https://github.com/cyberbotics/urdf2webots)
> - The [Blender Robotics Tools](https://github.com/robotology/blender-robotics-utils/) repository includes a number of useful tools, including a tool to export [URDF files from Blender.](https://github.com/robotology/blender-robotics-utils/tree/master?tab=readme-ov-file#urdftoblender)
> - [CoppeliaSim URDF Exporter](https://manual.coppeliarobotics.com/en/importExport.htm#urdf)
> - [Isaac Sim URDF Exporter](https://docs.omniverse.nvidia.com/isaacsim/latest/advanced_tutorials/tutorial_advanced_export_urdf.html)

**Viewing URDF & SDF Files**

- [Examples of Common URDF Launch Files](https://github.com/ros/urdf_launch)
- Web Viewer for URDF Files: [GitHub Repo](https://github.com/gkjohnson/urdf-loaders/) & [Live Website](https://gkjohnson.github.io/urdf-loaders/javascript/example/bundle/index.html)
- [View SDF Models in RViz](https://github.com/Yadunund/view_sdf_rviz)
- [Jupyterlab URDF Viewer](https://github.com/IsabelParedes/jupyterlab-urdf)

If you have an URDF tool you like please consider adding it to the list above!

---
### 🔗 Robot Modeling & URDF Workflow
[[Building a visual robot model from scratch — ROS2-Jazzy.md|Building a visual robot model from scratch]], [[Adding physical and collision properties — ROS2-Jazzy.md|Adding physical and collision properties]], [[Design-time considerations — Onshape to robot.md|Design-time considerations]], [[Building a movable robot model — ROS2-Jazzy.md|Building a movable robot model]], [[Configuration (config.json) — Onshape to robot.md|Configuration (config.json)]], [[Using URDF with robot_state_publisher (Python) — ROS2-Jazzy.md|Using URDF with robot_state_publisher (Python)]], [[Getting started — Onshape to robot.md|Getting started]]
