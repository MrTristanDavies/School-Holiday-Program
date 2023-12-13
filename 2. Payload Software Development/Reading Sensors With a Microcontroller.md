### Session 5: Reading Sensors With a Microcontroller

## Objectives
1. Download zip file with partially completed STM32 initialisation
2. Initialise internal temperature sensor
3. Understand the role of an ADC in data acquisition 
4. Read and display raw ADC data

## Requirements
1. STM32CubeIDE installed on device
2. Pen and paper
3. STM32L432KC Microcontroller with usb a to micro usb cable

## Resources


## Procedure
# 1.0 STM32IDE Project Initialisation
To begin our journey into learning how these complex devices are used, we first need to set up our devices for the correct functionality. Hence, we use STMCubeIDE to modify the pin functionalities.

1.	Download the *ReadSensWithMicro.proj.zip* file from the repository.

Insert image of file with red box around it and another after it with a right clicked version with a red box around the download.

2.	Unzip the STM32CubeIDE project file.

Insert image of right clicked file with unzip highlighted

3.	Open the STM32CubeIDE and navigate to File -> Open Project from File System… -> Directory

Insert Image showing this location

4.	Find the project file in your download location commonly in “Downloads” folder.

Insert image showing the selection of the project downloaded

5.	Expand the “Analog” category on the left side of the window and click on “ADC1”.

This is the configuration for the built in analogue to digital converter “ADC1”. This hardware peripheral measures analogue voltages and digitises them, storing the conversion result in a register for use in software. This allows you to write software that can respond to changing voltages or values from sensors that output their result as an analogue voltage level.

6.	Scroll through the ADC1 “Mode and Configuration” tab that just appeared and search for “IN17”. Click on the drop-down menu and select “Temperature Sensor Channel”.

We’re going to read from the L4’s built in internal temperature sensor instead of connecting external circuity to the one of the ADC input pins.

7.	We’re also going to use a GPIO pin as an output to turn drive the Nucleo board’s built in LED. In the “Pinout view” left click on the pin connected to “PB3” LED and select “GPIO_Output”.

8.	 Right click on the “PB3” pin, and give it a user label: “LED”

Now we’re going to set up the UART (universal asynchronous receiver-transmitter) serial communication peripheral which we will use to send messages to the computer to help with software development. 

The “VCP” (virtual com port) TX (transmit) and RX (receive) lines in the built in ST-LINK debugger are connected are connected to the “PA2” and “PA15” pins on the L4.

9.	Left click on “PA2” and select “USART_2TX”. 

10.	Left click on “PA15” and select “USART_2RX”.

11.	Now look to the left hand side and select the “connectivity” drop down menu and change the “mode” drop down the “Asynchronous”.

The “PA2” and “PA15” pins in the pinout view should now turn green as they have a valid configuration. 

You’re pinout view should look like this:

Insert image of correct green pinout map

12.	Look down in the “Parameter Settings” (Middle bottom pane) for “USART2” and make a note of the “Baud Rate” in your notebook. We’ll need to set our serial console viewer to the same settings to receive the messages later. 

You’re now finished configuring STM32 for the rest of the session.

# 2.0 C Code Fundamentals
