---
title: "Peripherals, Schematics, and Configuring Pins - Bootcamps"
source: "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998848246/Peripherals+Schematics+and+Configuring+Pins"
author:
published:
created: 2026-05-13
description:
tags:
  - "clippings"
---
## Peripherals, Schematics, and Configuring Pins

### Components and Communication

For this bootcamp there are 4 components being used.

- A potentiometer used as an input to control the motor.
- An Analog to Digital Converter (ADC) that converts the analog voltage from the potentiometer and generates a digital value sent using SPI.
- The microcontroller, the brain for this project that reads the digital ADC value and generates a Pulse Width Modulation (PWM) signal that controls the motor.
- The motor, the output of the system.

#### ADC and SPI

Analog to digital converters (ADCs) take an analog value and convert it to digital numbers. This peripheral is useful to interface with sensors, battery voltages, and potentiometers. For this bootcamp, you will be communicating with an external ADC using [SPI communication](https://uwarg-docs.atlassian.net/wiki/spaces/efs/pages/1995964446 "https://uwarg-docs.atlassian.net/wiki/spaces/efs/pages/1995964446"), a protocol that uses a clock signal and data transmission lines to communicate. This ADC will convert the analog voltage of a potentiometer into a digital signal (data in form of High “1” bits and Low “0” bits) sent back to the MCU (Microcontroller).

The ADC in the circuit board is an [MCP 3004](https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf "https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf") chip that communicates over Serial Peripheral Interface (SPI). SPI is a very common firmware protocol, documentation on what it is and how it works has been written in the [SPI Documentation Page](https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/1995964446 "https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/1995964446").

#### PWM and Motor Control

Timer modules are a hardware feature of embedded microcontrollers. They allow the program to delay without blocking other code from running. Timers are useful to implement PWM (Pulse Width Modulation signals), since PWM has very specific timing requirements for when the IO pin gets turned on and off. In this bootcamp the MCU will use the digital signal from the ADC to generate a specific PWM signal to control the motor.

Pulse Width Modulation (PWM) is a signal type that varies the duty cycle (Percent of the signal period with a "High" signal) to convey information. This is often used for motors and more documentation can be found in the [PWM Documentation Page](https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/1996783718 "https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/1996783718").

For this bootcamp your output will be a **50Hz.** signal with a **1ms to 2ms** on-time (5-10% Duty Cycle). The duty cycle will vary based on the reading of the ADC. This duty cycle and frequency is standard across many motors.

### Firmware Bootcamp Circuit Board Schematic

This bootcamp is made to run on an already designed and built circuit board. To tell the microcontroller which pins correspond to which peripheral (component), the 2021-Firmware-Bootcamp.ioc file in the STM32 Project will need to be configured.

When reading the circuit board do not despair if you do not understand what a component symbol means. The most important part of the schematic for firmware is how the components connect to the MCU.

For this schematic those connections are explicitly stated with their respective pins. In real tasks you may need to decide where the circuit schematic leads connect to the MCU and configure the pins based on the input and what each MCU pin is able to do.

Firmware Bootcamp Board Schematic:

The pin number on the MCU and its connection in the circuit are listed below:

<table><colgroup><col> <col></colgroup><tbody><tr><th rowspan="1" colspan="1"><div><p><strong>Pin</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>Use</strong></p><figure></figure></div></th></tr></tbody></table>

<table><colgroup><col> <col></colgroup><tbody><tr><th rowspan="1" colspan="1"><div><p><strong>Pin</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>Use</strong></p><figure></figure></div></th></tr><tr><td rowspan="1" colspan="1"><p>PB8</p></td><td rowspan="1" colspan="1"><p>SPI Chip Select (GPIO_Output)</p></td></tr><tr><td rowspan="1" colspan="1"><p>PB3</p></td><td rowspan="1" colspan="1"><p>SPI Clock Signal (SPI1_SCK)</p></td></tr><tr><td rowspan="1" colspan="1"><p>PA6</p></td><td rowspan="1" colspan="1"><p>SPI Input from the ADC (SPI1_MISO)</p></td></tr><tr><td rowspan="1" colspan="1"><p>PA7</p></td><td rowspan="1" colspan="1"><p>SPI Output to the ADC (SPI1_MOSI)</p></td></tr><tr><td rowspan="1" colspan="1"><p>PA8</p></td><td rowspan="1" colspan="1"><p>PWM Output to the Motor (TIM1_CH1)</p></td></tr></tbody></table>

### Configuring Pins and Peripherals

This chip by default will not have any of the pins we need configured. To configure them either find the pin you want to configure and click on it, or use the menu on the left and find what configuration you want it to be.

#### STM32 Cube IDE Device Configuration

Each of the pins from the schematic will need to be configured as the project you are given is blank.

**Tips:**

- To configure the SPI pins, use the Connectivity menu on the left side of the screen and set the SPI mode to “Full-Duplex Master” with Hardware NSS Signal Disabled. This will set up the pins in their default spot. To see what alternate pins are available for a specific configuration (eg. SPI1\_MOSI) use ctrl + left click on the currently configured pin to see. If the default setup does not match the schematic then you will need to change which pin is configured.
- It is easier to configure GPIO pins by clicking on the pin you want to configure and directly setting the mode than going through the menu.
- ==Pot means Potentiometer, a very legal variable resistor.==