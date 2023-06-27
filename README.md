# TwinDragon600-Electronics
Electronic description, pinout and manuals for the electronics used in Twin Dragon 600

Pin Configurations, jumper selection, CanBus and multi-MCU wiring to BTT CB1 embedded onto BTT Manta M5P for Twin Dragon 600

Components used:
1. BTT Manta M5P - 1
2. BTT CB1 (embed onto BTT Manta M5P) - 1
3. BTT EBB36 Can Module/Toolboard - 2
4. TMC5160 Stepper drivers - 5
5. MKS Gen L V2.1 - 1
6. TMC2209 stepper drivers - 2 (On the MKS GenL) + 2 (Present on the BTT EBB36's)
7. BTT HDMI5 Touch Display

## Setting up BTT Manta M5P + BTT CB1

### Initial Preparation

At the Initial stage, when needed to only access the CB1 module with USB power supply, a jumper is to be placed in the slot mentioned as 'VUSB' present between the micro HDMI port and the SOC-SD card slot.
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/791e50cf-759c-492f-b01c-6217e4d9f80c)

This should not be inserted when the board is supplied with 24V and fully functioning.

### Other Initial preparation and setting up jumpers

#### TMC Driver SPI Mode
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/eb977580-6a62-4721-bdbb-7048f962c450)

The first row are the defined pin for the drivers, which are either high or low when shorted or unshorted to establish different mode of communication. The second row are defined with the SPI modes, with the namings of 'MISO', 'CS', 'SCK' and 'MOSI' when read from left to right. Since we use the TMC5160 driver, it specifically operates only on the SPI mode. Insert the jumpers corresponding to its parallel pins only on the 1st and the 2nd row as shown in the image.

#### Driver Voltage selection
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/f63e0da7-5936-4e4a-a355-ef9f8fcb7f29)

Since the TMC5160 operates only on SPI mode, which is specifically for achieving faster communication and higher speeds, it needs an operating voltage of around 48V. The manta M5P has seperte pins for regular voltage of 24V and high voltage of 48V, that is to be jumped to the common pin of voltage supply to the drivers. We jump the HV pin in the left to the middle pin of supply in order to provide 48V to the drivers, as shown in the image above.

#### Setting up jumper for probe activation
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/b9c4c061-bb4c-4f44-b8c9-ed8ce8ce50c2)

The pin for probe used here is the IND-probe pin on Manta M5P, and the jumper is placed on the two pins beside the probe pins as shown in the image above, to enable 24V supply to the ABL board.

#### Setting up Jumper for CANBUS communication
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/a7eed294-be88-430b-afcb-59b987539cb7)

At the bottom-left corner of the board, a small jumper is to be placed on the pins that mention '120R' depicting the 120 ohms resistance that is applied on the CAN Low and High communication pins. This is a crucial pin for the setting up of the CAN communication of the motherboard and toolboard.

## Setting up of BTT EBB36 CAN module/Toolboard

### Initial preparation
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/dcb284a4-73b8-4f71-b525-098fa84ddfd1)

After the motherboard is powered on, the yellow-green LED1 lights will light up, indicating a normal power supply. The VUSB on the right side of the board is the power selection terminal. Only when using USB to supply power to the motherboard or need to supply power through USB, do you need to use the jumper cap to connect VUSB.

#### Setting up Jumper for CANBUS communication
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/bfd6ef81-0449-4d2a-8653-4c20e432c70f)

Similar to the BTT Manta M5P, the Support communication via CAN or USB. The terminal resistor 120R of CAN can be selected through a jumper cap, and it reserves a CAN expansion interface.

#### Placing of Heatsink
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/0ebd0b78-d184-49d5-be39-2dbbd0ac9181)


Place the Heatsink onto the TMC2209 driver chip present on the board which is already embedded onto it as shown in the image above.

## Setting up of MKS GenL V2.1 for side extruder motors

### Setting up jumpers for enabling UART mode
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/c7aacc1b-fbd7-40ce-a9b2-0361d0976191)

Since we use the TMC2209 for the side extruder motors similar to the main extruder motors, we set the drivers in UART mode

## Wiring and Connections
![Twin Dragon 600 Wiring](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/359a2742-e5c0-4a0e-8f93-3b0dcc5a76f8)

The overall connections of all the Electrical and Electronic components are present in the image above

### BTT Manta M5P Pin connections
![BTT manta M5P pin connections](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/c9711b64-c066-4500-88e6-daba4909f991)

### EBB36 Pin connections
![EBB36 pin connections](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/497accd8-bd5b-4b3f-a62a-ec1e154168e3)

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/912fc072-66f3-47c0-b103-045449d52ce3)

The setting up of CANBUS communication in the right angle to avoid confusion

### MKS GenL V2.1 Pin Conections
![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/a165a7d3-6e1a-4e74-b23a-d65897767c25)

In the above image, the pin connections of side extruder motors are given, along with additional ports for the extruder filament sensors
