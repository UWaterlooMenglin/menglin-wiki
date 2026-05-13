# Embedded Flight Software Bootcamp - High-Level Overview

This document provides a consolidated overview of the Embedded Flight Software Bootcamp, outlining its objectives, core technologies, development workflow, and key resources. It aims to interconnect the various bootcamp modules and provide a quick reference for participants.

## 1. Bootcamp Objectives

*   Work with C logic and embedded programming concepts.
*   Familiarization with STM32 Cube IDE and microcontroller configuration.
*   Understanding SPI communication protocol.
*   Learning about PWM signals and their generation.
*   Proficiency in Git for code revisions and GitHub for code reviews.

## 2. Challenge: Implement a Motor Tester

The main challenge involves building a motor tester by:
*   Reading a potentiometer value via an external ADC chip using SPI.
*   Converting this analog input into a PWM signal.
*   Controlling a motor's speed/position with the generated PWM signal.

*Related Files:* [[Challenge - Bootcamps]]

## 3. Core Technologies and Concepts

### Microcontroller & Development Environment
*   **Microcontroller:** STM32 (nucleof072rb)
*   **Integrated Development Environment (IDE):** [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html)
    *   *Note:* Ensure you use recommended version (e.g., 1.19.0) and sign in.
*   **Hardware Abstraction Layer (HAL):** STM32CubeIDE automatically generates HAL code for peripheral configuration.

### Peripherals & Communication Protocols
*   **Analog-to-Digital Converter (ADC):** Converts analog voltage (potentiometer) to digital values.
    *   *Chip Used:* [MCP3004/3008](https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf)
*   **Serial Peripheral Interface (SPI):** A synchronous serial communication interface used for short-distance communication, primarily in embedded systems.
    *   *Usage:* Communicating with the external ADC.
*   **Timers (TIM):** Hardware features for timing operations, crucial for PWM generation.
*   **Pulse Width Modulation (PWM):** A modulation technique used to control power to electrical devices (like motors) by varying the duty cycle of a signal.
    *   *Requirements:* 50Hz signal, 1ms to 2ms on-time (5-10% duty cycle).
*   **General Purpose Input/Output (GPIO):** Configurable pins for basic digital input/output.

## 4. Development Workflow

The bootcamp follows a structured process:

1.  **Initial Onboarding:** Complete pre-bootcamp instructions, schedule EFS lead meeting, send onboarding email.
    *   *Related Files:* [[Embedded Flight Software Bootcamp - Bootcamps]]
2.  **Development Environment & Git Setup:**
    *   Fork the [UWARG/embedded-bootcamp](https://github.com/UWARG/embedded-bootcamp) repository.
    *   Install and sign into [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html).
    *   Understand Git fundamentals (fork, PRs) using [Our Git Tutorial](https://uwarg-docs.atlassian.net/l/c/qbC8L1kc).
    *   *Related Files:* [[Setting up the Dev Environment and Git - Bootcamps]]
3.  **Project Import & MCU Configuration:**
    *   Clone your forked repository.
    *   Import the project into STM32CubeIDE.
    *   Open and configure the `nucleof072rb.ioc` file using the Device Configuration Tool.
    *   *Related Files:* [[Opening STM32 Cube IDE - Bootcamps]]
4.  **Pin Configuration (based on Schematic):**
    *   Analyze the provided schematic (`fwTrainingRev3.pdf`) to identify pin connections between MCU, ADC, and motor.
    *   Configure MCU pins (e.g., PB8 as SPI Chip Select, PB3 as SPI Clock, PA6 as SPI MISO, PA7 as SPI MOSI, PA8 as PWM Output) in the `.ioc` file.
    *   *Related Files:* [[Peripherals, Schematics, and Configuring Pins - Bootcamps]]
5.  **Peripheral Configuration (SPI & TIM):**
    *   **SPI:** Configure SPI1 (e.g., Data Size, First Bit, Clock Polarity/Phase, Prescaler) based on the ADC datasheet.
    *   **Timers (PWM):** Configure TIM1 for PWM generation (e.g., Internal Clock, Prescaler, Period) to achieve the required 50Hz and 5-10% duty cycle.
    *   *Related Files:* [[Code Generation and Coding for the MCU - Bootcamps]]
6.  **Coding the MCU Behavior:**
    *   Write C code within `USER CODE BEGIN/END` blocks in `main.c`.
    *   Implement **ADC Communication:** Use HAL functions for full-duplex SPI communication with the ADC, controlling the CS line, and reading relevant bits from the ADC.
    *   Implement **PWM Signal Conversion:** Convert the ADC digital value to timer counts and set the compare register for PWM output, ensuring the correct duty cycle range.
    *   *Related Files:* [[Code Generation and Coding for the MCU - Bootcamps]]
7.  **Debugging & Verification:**
    *   Build the project in STM32CubeIDE to catch compiler errors.
    *   Physical testing on the circuit board (with team lead).
    *   *Related Files:* [[Code Generation and Coding for the MCU - Bootcamps]]
8.  **Submission & Review:**
    *   Create a Pull Request on GitHub (e.g., `Bootcamp: YOURNAME`).
    *   Request code review from EFS team leads.
    *   *Related Files:* [[Code Generation and Coding for the MCU - Bootcamps]]

## 5. Learning Resources

*   *Related Files:* [[Learning Resources - Bootcamps]]
*   [ADC Datasheet (MCP3008.pdf)](https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf)
*   [HAL Function APIs (UM1785)](https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf)
*   [HAL User Manual (RM0090)](https://www.st.com/resource/en/reference_manual/rm0090-stm32f405415-stm32f407417-stm32f427437-and-stm32f429439-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)
*   [UWARG Embedded Bootcamp GitHub Repository](https://github.com/UWARG/embedded-bootcamp)
*   [UWARG Git Tutorial](https://uwarg-docs.atlassian.net/l/c/qbC8L1kc)
*   [UWARG Code Style Guide](https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/1827635203)
*   **External Learning Materials:**
    *   [How to Control LEDs on the Arduino](https://www.circuitbasics.com/arduino-basics-controlling-led/#:~:text=To%20turn%20on%20an%20LED,the%20HIGH%20and%20LOW_states.)
    *   [STM32 Guide #2: Registers + HAL (Blink example)](https://www.youtube.com/watch?v=Hffw-m9fuxc&ab_channel=MitchDavis)
    *   [STM32 Guide #3: PWM + Timers](https://www.youtube.com/watch?v=AjN58ceQaF4&t=7s&ab_channel=MitchDavis)
    *   [Basics of Analog-to-Digital Converters](https://www.arrow.com/en/research-and-events/articles/engineering-resource-basics-of-analog-to-digital-converters)
    *   [STM32 IDE Intro](https://smartsolutions4home.com/how-to-program-stm32/)
    *   [Are You Reading the Datasheet?](https://embedjournal.com/are-you-reading-the-datasheet/)

## 6. Best Practices

*   **Code Style:** Adhere to the team's [code style guide](https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/1827635203).
*   **Git Commits:** Commit frequently after implementing functionality or reaching stable points.
*   **Ask for Help:** Don't hesitate to ask questions in Discord or use Google as a resource.