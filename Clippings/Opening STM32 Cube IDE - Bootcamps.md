---
title: "Opening STM32 Cube IDE - Bootcamps"
source: "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998782632/Opening+STM32+Cube+IDE"
author:
published:
created: 2026-05-13
description:
tags:
  - "clippings"
---
## Opening STM32 Cube IDE

For the STM32 microcontrollers we use, there is a specific IDE that is used to configure the microcontrollers, write code for them, and debug using the hardware. For this bootcamp and when you are writing drivers as a task, you will be using the [STM32 CUBE IDE](https://www.st.com/en/development-tools/stm32cubeide.html "https://www.st.com/en/development-tools/stm32cubeide.html").

1. Clone your forked bootcamp into a folder
![image-20240916-235713.png](blob:https://uwarg-docs.atlassian.net/98ea1ece-ae49-48b4-8dea-6355dd5559f5#media-blob-url=true&id=50b92cc8-66d6-4308-b16a-45bea1ddc4c7&collection=contentId-1998782632&contextId=1998782632&width=2561&height=1576&alt=image-20240916-235713.png&clientId=ba18b5fd-aac8-4e36-a039-8a3dab01bb0c)
2. Import the project (File > Import… > Existing Projects into Workspace > Next)
![image-20240916-235935.png](blob:https://uwarg-docs.atlassian.net/0b140c55-e23f-4cc2-9083-272bb3001e06#media-blob-url=true&id=28b72c0e-0602-4f0e-81e6-627859337730&collection=contentId-1998782632&contextId=1998782632&width=3834&height=2038&alt=image-20240916-235935.png&clientId=ba18b5fd-aac8-4e36-a039-8a3dab01bb0c)
3. Set the root directory to be the folder in which you cloned into. Make sure the *nucleof072rb* project is checked. Click *Finish.*

This IDE can generate code to configure the microcontroller’s pins and that is exactly how we will start.

## STM32 Cube IDE Device Configuration Tool

Double click on the “nucleof072rb.ioc” file, and this will bring you to the device configuration tool.

First make sure you are in the “Pinout & Configuration” menu and your display matches the one below:

Base Chip Configuration

This is the microcontroller chip that is being used in this bootcamp. Note that the project you are given will have some initialized pins (seen above). You do not need to worry about those as they are configured by default.