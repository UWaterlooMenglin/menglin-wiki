---
title: "Challenge - Bootcamps"
source: "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998061593/Challenge"
author:
published:
created: 2026-05-13
description:
tags:
  - "clippings"
---
## Challenge

## Your Challenge: Implement a Motor Tester

### Background

One of the biggest things that makes embedded programming interesting is working to control both hardware and software. There are several low-level (closer to the physical hardware components) peripherals on-board the microcontrollers for interfacing with various devices. The low-level libraries you will be working with for this bootcamp are the serial peripheral interface ([SPI](https://uwarg-docs.atlassian.net/wiki/spaces/efs/pages/1995964446 "https://uwarg-docs.atlassian.net/wiki/spaces/efs/pages/1995964446")) and the timers (TIM).

## Instructions

Your task is to input a potentiometer value from 0 to 3.3V and convert it to a PWM signal to control a motor. The potentiometer is connected to an external ADC chip which sends data to the MCU over [SPI](https://uwarg-docs.atlassian.net/wiki/spaces/efs/pages/1995964446 "https://uwarg-docs.atlassian.net/wiki/spaces/efs/pages/1995964446"). Motor testers are useful for determining servo motor range, continuous rotation motor speed, prototype testing, and centering servos.

![efs bootcamp setup.drawio (3)-20240113-195744.png](blob:https://uwarg-docs.atlassian.net/2f7c1cfc-3abd-4f50-8409-3baa7e3a00f5#media-blob-url=true&id=a6fa1ea5-b42a-4ceb-a7c1-773065b7194a&collection=contentId-1998061593&contextId=1998061593&width=1149&height=1118&alt=efs%20bootcamp%20setup.drawio%20(3)-20240113-195744.png&clientId=ba18b5fd-aac8-4e36-a039-8a3dab01bb0c)

Documentation is provided for each step in the process in the next bootcamp pages.

1. Fork [this repository](https://github.com/UWARG/embedded-bootcamp "https://github.com/UWARG/embedded-bootcamp") so you can edit it (See [Setting up the Dev Environment and Git](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998782676 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998782676"))
2. [Set up development environment](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998782676 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998782676")
3. [Open the project in the STM32 Cube IDE](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998782632 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998782632")
4. [Configure Microcontroller (.ioc) file pins based on schematic](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998848246 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998848246")
5. [Configure SPI peripheral (ADC)](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457")
6. [Configure timer for PWM signal](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457")
7. [Write code to convert ADC input to motor control signal](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457")
8. [Debug all Compiler Errors](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457")
9. [Create a git pull request](https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457 "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457") and message in the your fw-onboarding thread in the WARG Discord to have it reviewed
10. Once approved, come into the bay to test your code if you are on campus!

A preliminary schematic of the circuit board created for this bootcamp:

fwTrainingRev3.pdf