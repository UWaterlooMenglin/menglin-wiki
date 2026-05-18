---
title: "Setting up the Dev Environment and Git - Bootcamps"
source: "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998782676/Setting+up+the+Dev+Environment+and+Git"
author:
published:
created: 2026-05-13
description:
tags:
  - "clippings"
---
## Setting up the Dev Environment and Git

### Git

The code for the embedded bootcamp is hosted on [GitHub](https://www.github.com/UWARG/embedded-bootcamp "https://www.github.com/UWARG/embedded-bootcamp"). You will have to **fork** the repository to make your changes and once you’re done open a **PR** (Pull Request). If you don't know what Git or GitHub is, or how to use it, please read [Our Git Tutorial](https://uwarg-docs.atlassian.net/l/c/qbC8L1kc "https://uwarg-docs.atlassian.net/l/c/qbC8L1kc").

### Development Environment Setup

WARG firmware development requires some setup before writing code for the microcontrollers we use. For the bootcamp (and future work), you will need the following:

- [STM32 Account](https://www.st.com/cas/login "https://www.st.com/cas/login")
- [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html "https://www.st.com/en/development-tools/stm32cubeide.html")
	- NOTE: This guide is currently written for STM32CubeIDE 1.19.0 and below. For version 2.0+, the app is split into CubeIDE and CubeMX. As 2.0 is still very new, we recommend installing 1.19.0 for now. Refer to the image below for selecting a version.
		- ![image-20260107-033740.png](blob:https://uwarg-docs.atlassian.net/fab77d9f-4b26-4e8b-a55d-14eed1c5f08c#media-blob-url=true&id=3720e920-3eb6-408a-b704-8a0f8c3795ae&collection=contentId-1998782676&contextId=1998782676&width=950&height=178&alt=image-20260107-033740.png&clientId=ba18b5fd-aac8-4e36-a039-8a3dab01bb0c)

Once you have made an STM32 account and downloaded the IDE, **you must sign into your account in the IDE**.

For STM32CubeIDE versions before 1.17.0, click on “myST“ in the top tool bar to do so.

Not signed in. Notice the “myST“ in the top tool bar.

Signed in. Notice the “Hello <username>“ in the top tool bar.

For STM32CubeIDE version 1.17.0 and after, see the post below:

If you do not log in, the IDE will not be able to download files necessary to complete the next configuration steps.

Note, [Dev Environment Setup Guide](https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/565215233 "https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/565215233") gives you a complete description of all the tools that EFS uses, but you **do not need** these for the bootcamp.