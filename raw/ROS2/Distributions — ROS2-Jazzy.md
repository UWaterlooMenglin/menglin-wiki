---
title: "Distributions — ROS 2 Documentation: Jazzy  documentation"
source: "https://docs.ros.org/en/jazzy/Releases.html"
author:
published: 2026-05-21
created: 2026-06-08
description:
tags:
  - "clippings"
---
**You're reading the documentation for an older, but still supported, version of ROS 2. For information on the latest version, please have a look at [Lyrical](https://docs.ros.org/en/lyrical/Releases.html).**

## Distributions

## What is a Distribution?

A ROS distribution is a versioned set of ROS packages. These are akin to Linux distributions (e.g. Ubuntu). The purpose of the ROS distributions is to let developers work against a relatively stable codebase until they are ready to roll everything forward. Therefore once a distribution is released, we try to limit changes to bug fixes and non-breaking improvements for the core packages (every thing under ros-desktop-full). That generally applies to the whole community, but for “higher” level packages, the rules are less strict, and so it falls to the maintainers of a given package to avoid breaking changes.

## List of Distributions

Below is a list of current and historic ROS 2 distributions. Rows in the table marked in blue are the currently supported distributions.

| Distro | Release date | Logo | EOL date | ROS Boss |
| --- | --- | --- | --- | --- |
| [Lyrical Luth](https://docs.ros.org/en/jazzy/Releases/Release-Lyrical-Luth.html) | May 22, 2026 | ![Lyrical logo](https://docs.ros.org/en/jazzy/_images/lyrical-small.png) | May 2031 | [Shane Loretz](https://github.com/sloretz) |
| [Kilted Kaiju](https://docs.ros.org/en/jazzy/Releases/Release-Kilted-Kaiju.html) | May 23, 2025 | ![Kilted logo](https://docs.ros.org/en/jazzy/_images/kilted-small.png) | December 2026 | [Scott K Logan](https://github.com/cottsay) |
| [Jazzy Jalisco](https://docs.ros.org/en/jazzy/Releases/Release-Jazzy-Jalisco.html) | May 23, 2024 | ![Jazzy logo](https://docs.ros.org/en/jazzy/_images/jazzy-small.png) | May 2029 | [Marco A. Gutiérrez](https://github.com/marcoag) |
| [Iron Irwini](https://docs.ros.org/en/jazzy/Releases/Release-Iron-Irwini.html) | May 23, 2023 | ![Iron logo](https://docs.ros.org/en/jazzy/_images/iron-small.png) | December 4, 2024 | [Yadunund Vijay](https://github.com/Yadunund) |
| [Humble Hawksbill](https://docs.ros.org/en/jazzy/Releases/Release-Humble-Hawksbill.html) | May 23, 2022 | ![Humble logo](https://docs.ros.org/en/jazzy/_images/humble-small.png) | May 2027 | [Christophe Bédard](https://github.com/christophebedard) / [Audrow Nash](https://github.com/audrow) |
| [Galactic Geochelone](https://docs.ros.org/en/jazzy/Releases/Release-Galactic-Geochelone.html) | May 23, 2021 | ![Galactic logo](https://docs.ros.org/en/jazzy/_images/galactic-small.png) | December 9, 2022 | [Scott Logan](https://github.com/cottsay/) |
| [Foxy Fitzroy](https://docs.ros.org/en/jazzy/Releases/Release-Foxy-Fitzroy.html) | June 5, 2020 | ![Foxy logo](https://docs.ros.org/en/jazzy/_images/foxy-small.png) | June 20, 2023 | [Jacob Perron](https://github.com/jacobperron) / [Dharini Dutia](https://github.com/quarkytale) |
| [Eloquent Elusor](https://docs.ros.org/en/jazzy/Releases/Release-Eloquent-Elusor.html) | November 22, 2019 | ![Eloquent logo](https://docs.ros.org/en/jazzy/_images/eloquent-small.png) | November 2020 | [Michael Carroll](https://github.com/mjcarroll) |
| [Dashing Diademata](https://docs.ros.org/en/jazzy/Releases/Release-Dashing-Diademata.html) | May 31, 2019 | ![Dashing logo](https://docs.ros.org/en/jazzy/_images/dashing-small.png) | May 2021 | [Steven! Ragnarök](https://github.com/nuclearsandwich) |
| [Crystal Clemmys](https://docs.ros.org/en/jazzy/Releases/Release-Crystal-Clemmys.html) | December 14, 2018 | ![Crystal logo](https://docs.ros.org/en/jazzy/_images/crystal-small.png) | December 2019 | [Steven! Ragnarök](https://github.com/nuclearsandwich) |
| [Bouncy Bolson](https://docs.ros.org/en/jazzy/Releases/Release-Bouncy-Bolson.html) | July 2, 2018 | ![Bouncy logo](https://docs.ros.org/en/jazzy/_images/bouncy-small.png) | July 2019 | [Mikael Arguedas](https://github.com/mikaelarguedas) / [Steven! Ragnarök](https://github.com/nuclearsandwich) |
| [Ardent Apalone](https://docs.ros.org/en/jazzy/Releases/Release-Ardent-Apalone.html) | December 8, 2017 | ![Ardent logo](https://docs.ros.org/en/jazzy/_images/ardent-small.png) | December 2018 | [Steven! Ragnarök](https://github.com/nuclearsandwich) |
| [beta3](https://docs.ros.org/en/jazzy/Releases/Beta3-Overview.html) | September 13, 2017 |  | December 2017 |  |
| [beta2](https://docs.ros.org/en/jazzy/Releases/Beta2-Overview.html) | July 5, 2017 |  | September 2017 |  |
| [beta1](https://docs.ros.org/en/jazzy/Releases/Beta1-Overview.html) | December 19, 2016 |  | Jul 2017 |  |
| [alpha1 - alpha8](https://docs.ros.org/en/jazzy/Releases/Alpha-Overview.html) | August 31, 2015 |  | December 2016 |  |

## Future Distributions

For details on upcoming features see the [roadmap](https://docs.ros.org/en/jazzy/The-ROS2-Project/Roadmap.html).

There is a new ROS 2 distribution released yearly on May 23rd ([World Turtle Day](https://www.worldturtleday.org/)).

| Distro | Release date | Logo | EOL date |
| --- | --- | --- | --- |
| [Makoa Mata-mata](https://docs.ros.org/en/jazzy/Releases/Release-Makoa-Mata-mata.html) | May 2027 | TBD | Dec 2028 |

## Rolling Distribution

[ROS 2 Rolling Ridley](https://docs.ros.org/en/jazzy/Releases/Release-Rolling-Ridley.html) is the rolling development distribution of ROS 2. It is described in [REP 2002](https://reps.openrobotics.org/rep-2002/) and was first introduced in June 2020.

The Rolling distribution of ROS 2 serves two purposes:

1. it is a staging area for future stable distributions of ROS 2, and
2. it is a collection of the most recent development releases.

As the name implies, Rolling is continuously updated and **can have in-place updates that include breaking changes**. We recommend that most people use the most recent stable distribution instead (see ).

Packages released into the Rolling distribution will be automatically released into future stable distributions of ROS 2. [Releasing a ROS 2 package](https://docs.ros.org/en/jazzy/How-To-Guides/Releasing/Releasing-a-Package.html) into the Rolling distribution follows the same procedures as all other ROS 2 distributions.

## Cross-Distribution Communications

Nodes are not guaranteed to be able to communicate across distributions. For example, a node built & running against Humble is not guaranteed to be able to communicate correctly with a node built & running against Iron. It may or may not work, but it is not supported and should not be relied upon. Note that [cross-vendor (single-distro) communications are also not guaranteed](https://docs.ros.org/en/jazzy/Concepts/Intermediate/About-Different-Middleware-Vendors.html#different-middleware-vendors-cross-vendor-communication).