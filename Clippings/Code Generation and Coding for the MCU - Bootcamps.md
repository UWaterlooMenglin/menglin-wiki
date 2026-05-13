---
title: "Code Generation and Coding for the MCU - Bootcamps"
source: "https://uwarg-docs.atlassian.net/wiki/spaces/BOOT/pages/1998815457/Code+Generation+and+Coding+for+the+MCU"
author:
published:
created: 2026-05-13
description:
tags:
  - "clippings"
---
## Code Generation and Coding for the MCU

Now that all the peripheral pins are in their respective modes, They will need to be configured more specifically for this application and the actual coding can begin.

### Configuring SPI Communication for this ADC

The microcontroller will need to tell the ADC to start converting the voltage value and then receive the digital input over SPI.

The SPI communication will need to be further configured. To configure it go to the.ioc file, find SPI1 in the Connectivity menu on the left:

![](blob:https://uwarg-docs.atlassian.net/b1bfcf58-8bb4-413a-8122-e3408e65cd47#media-blob-url=true&id=031db09a-483f-4ccf-91d4-cbc45f27bdd4&collection=contentId-1998815457&contextId=1998815457&width=840&height=714&alt=&clientId=ba18b5fd-aac8-4e36-a039-8a3dab01bb0c)

Then, configure the parameters:

- Data Size
- First Bit
- Clock Polarity
- Clock Phase

To do so, do the following:

1. Understand what each parameter does/means
2. Look in the [ADC datasheet](https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf "https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf") under sections 5.0 and 6.1 to learn how the ADC communicates
3. Draw conclusions and set appropriate values

Also, it is good to note that the MCU can run much faster than the ADC and outpace it. Add a Prescaler of 16 or greater in the configuration of SPI1 to keep the baud rate reasonable for the ADC.

The Hal library automatically generates the base code required to run the configuration you set when you save the.ioc file. You do want the IDE to generate code for you.

Yes, Make the IDE do work for you.

### Configure the Timer (PWM)

To configure it go to the.ioc file, find TIM1 in the Timers menu on the left:

TIM1 Base Configuration

To start ensure that the channel (pin connected to timer) you chose is in the “PWM Generation CH#” mode. The clock source should be “Internal Clock” as we are using the clock that is built into the MCU.

The Prescaler and Period of the timer will need to be configured to meet the **50Hz.** (period of 20ms) and **1ms to 2ms** on-time (5-10% duty cycle) required to drive the motor.

The timer works as a counter, it counts up to the set counter period value before changing the output. The maximum number it can count to is 65535, or the maximum 2 byte number (uint16\_t of 0xFFFF). The prescaler will slow down the system clock by dividing by (prescaler + 1) that way the speed is unaffected if prescaler = 0.

The equations based on the input clock speed are:

Counter Period and Prescaler Equations

For this system the input clock speed is 48.0MHz. and the desired frequency is 50.0Hz.

Hint: A lower prescaler value with a higher counter period value will produce more accurate results.

## Coding in STM32 Cube IDE

Once you have generated the code for the SPI and TIM configuration, you can find those values and settings will show up in the Core->Src for.c and Core->Inc for.h files in the project. Since you have configured them they should not need to be changed, however you can change the configuration using the spi and tim files.

To code the MCU behavior find the main.c file in Core->Src and open it:

The IDE may ask if you want to change to a different view, you can, it will show you tools that are more useful for C/C++ programming.

When programming in the STM32 Cube IDE your code must be written in between the USER CODE BEGIN and USER CODE END comments. Otherwise it will be erased whenever you generate code using the.ioc file.

Valid and Invalid Code Placement

The basic main file contains 4 sections:

- Before main:
	- A place to declare constants, additional function prototypes, global variables
- Inside main outside t ==he while(1) loo== p:
	- A place for any setup or functions you want to run once before the loop
- Inside the while loop:
	- Code that will be run repeatedly and often contains the main system behavior
		- Please add the following line here at the end of the user code section to ensure the MCU doesn’t overload the ADC:
		- `HAL_Delay(10);`
- After main:
	- Where you write functions that match any function prototypes you have added

### Coding ADC Communication

To find the functions you will use to send and read messages from the ADC, either find the stm32f0xx\_hal\_spi.h file in the Drivers->STM32F0xx\_HAL\_Driver->Inc directory and read the function prototypes at the bottom or visit the [HAL Function APIs](https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf "https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf") and look for the SPI input and output functions (SPI starts from p450). Also, Google is a good learning resource, as there are so many people who give examples of how to use SPI to communicate between hardware.

It is good to note that this ADC requires full duplex mode SPI communication, meaning that information will be sent to the ADC and read from it at the same time. You will need to use the SPI function that can both send and receive data.

The diagrams in section 6.1 of the [ADC datasheet](https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf "https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf") show the length and timing of the communication. Section 5 has a table that shows what bits to send to select the channel and mode.

For this circuit board, you can check which ADC channel the potentiometer is connected to from the schematic. The mode is differential if it is comparing 2 signals, single if it comparing one signal to the ground input.

Don’t forget that the ADC requires specific behavior for the CS line that is connected to the GPIO pin you set. Information for controlling a GPIO pin can be found in the [HAL Function APIs](https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf "https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf") (GPIO starts from p196).

### Converting ADC value to PWM signal

The main behavior of the system will be written here. The ADC value will need to be converted into a number of counts for the timer counter.

To change what the timer outputs is a bit difficult, We will need to set the compare register to the value we calculate for the number of “on counts” from the ADC. The compare register compares the counter value and if the counter is below the compare register value it will output a “HIGH” signal. There is a helpful macro defined in Drivers->Inc->stm32f0xx\_hal\_tim.h that will directly set the compare register.

**Hints:**

- Only 10 of the bits read from the ADC contain useful data (LSB/MSB determines which bits), the rest will need to be ignored.
- The ADC digital value will range from the maximum to minimum value 10 bits can hold.
	- (What is the largest number that 10 bits can hold?)
- The timer will need to be started only once in the program.
- Remember that the duty cycle must range from 5-10% of the total period or 1-2ms of on time and the ADC value will need to be converted to counts.

## Best Practices

For the Firmware team we follow a naming and [code style guide](https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/1827635203 "https://uwarg-docs.atlassian.net/wiki/spaces/ZP/pages/1827635203") to make our code more uniform and readable

It is also a good habit to (git) commit after each piece of functionality you implement and at points where your code is stable. That way if you need to revert your changes, all your code is saved.

### Debugging

To start debugging you can build the project using the button in the IDE shown below:

Errors will be shown at the bottom of the screen. This will not catch behavior issues, just will catch compiler errors. The behavior will be checked by a firmware team member and later you may be able to come to the bay and run your code on the physical board.

### Submission

Because this is the firmware subteam the code we write can control physical hardware. To submit this bootcamp you will be asked to have your code reviewed by a member of the team and when they are satisfied with it you can book a time to come into the WARG bay to test and debug your code on the physical setup.

To submit your work for review, create a pull request of your fork against the [UWARG/embedded-bootcamp](https://github.com/UWARG/embedded-bootcamp "https://github.com/UWARG/embedded-bootcamp") repository. Name your pull request `Bootcamp: YOURNAME`. Tell the responsible team lead that you've completed the bootcamp in the `#Bootcamp` Discord channel and they will have someone review your submission. You may be asked to revise some things.

### General Hints

- ==Look at the HAL\_TIM\_ and \_\_HAL\_TIM\_ functions to access the timer. The== [==HAL User Manual==](https://www.st.com/resource/en/reference_manual/rm0090-stm32f405415-stm32f407417-stm32f427437-and-stm32f429439-advanced-armbased-32bit-mcus-stmicroelectronics.pdf "https://www.st.com/resource/en/reference_manual/rm0090-stm32f405415-stm32f407417-stm32f427437-and-stm32f429439-advanced-armbased-32bit-mcus-stmicroelectronics.pdf") [==HAL Function APIs==](https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf "https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf") ==will be particularly useful here.==
- For SPI communication look at the SPI IO operation function in the [HAL User Manual](https://www.st.com/resource/en/reference_manual/rm0090-stm32f405415-stm32f407417-stm32f427437-and-stm32f429439-advanced-armbased-32bit-mcus-stmicroelectronics.pdf "https://www.st.com/resource/en/reference_manual/rm0090-stm32f405415-stm32f407417-stm32f427437-and-stm32f429439-advanced-armbased-32bit-mcus-stmicroelectronics.pdf") [HAL Function APIs](https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf "https://www.st.com/resource/en/user_manual/um1785-description-of-stm32f0-hal-and-lowlayer-drivers-stmicroelectronics.pdf").
- The electrical schematic is useful for determining which pins should be configured to which peripheral.
- Don’t be shy to learn from Google or shoot your question in discord if any of the resource provided in this bootcamp document are not helping you.