# TwinDragon600-Electronics

### For the Combination of BTT Manta M5P + BTT CB1 + BTT EBB36 + MKS Gen L V2.1

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

### For the Combination of BTT Manta M8P + BTT CB1 + RP2040 based toolboard

Pin Configurations, jumper selection, CanBus and multi-MCU wiring to BTT CB1 embedded onto BTT Manta M8P for Twin Dragon 600

Components used:
1. BTT Manta M8P - 1
2. BTT CB1 (embed onto BTT Manta M8P) - 1
3. RP2040 based Can Module/Toolboard - 2
4. TMC5160 Stepper drivers - 5
5. TMC2209 stepper drivers - 2 (On the MKS GenL) + 2 (Present on the Toolboards)
6. BTT HDMI5 Touch Display

## Setting up BTT Manta M5P + BTT CB1 + BTT EBB36 + MKS Gen L V2.1

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

## Setting up BTT Manta M8P + BTT CB1 + RP2040 based toolboard

### Initial Preparation

At the Initial stage, when needed to only access the CB1 module with USB power supply, a jumper is to be placed in the slot mentioned as 'VUSB' present behind the Type-C port. After the M8P motherboard is powered on, the D32 red light on the left side of the MCU will light up, indicating that the power supply is normal.

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/929dbe3d-8957-4326-9336-440fd2051fec)

### Other Initial preparation and setting up jumpers

#### TMC Driver SPI Mode

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/872914e8-7322-4a7e-b62b-000565df552a)

The first row are the defined pin for the drivers, which are either high or low when shorted or unshorted to establish different mode of communication. The second row are defined with the SPI modes, with the namings of 'MISO', 'CS', 'SCK' and 'MOSI' when read from left to right. Since we use the TMC5160 driver, it specifically operates only on the SPI mode. Insert the jumpers corresponding to its parallel pins only on the 1st and the 2nd row as shown in the image.

#### TMC Driver UART Mode

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/3169c8fd-00ae-4d24-b94d-a3c7ebc864bc)

The given set of pin to short is the CS pin that enables only the uart mode.


#### Driver Voltage selection

For High Voltage selection(48V):

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/809227d3-46d4-4e38-98c4-3f301c4ca9cd)

Since the TMC5160 operates only on SPI mode, which is specifically for achieving faster communication and higher speeds, it needs an operating voltage of around 48V. The manta M8P has seperte pins for regular voltage of 24V and high voltage of 48V, that is to be jumped to the common pin of voltage supply to the drivers. We jump the HV pin in the left to the middle pin of supply in order to provide 48V to the drivers, as shown in the image above.

For normal Voltage selection (24V):

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/70aace2f-17dc-497d-9a33-75885de8d74c)

This voltage selection can be used when using a regular TMC2209 on the UART mode

#### Setting up jumper for probe activation

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/8da7f294-f5f2-4657-b814-a4832fe14caa)

The pin for probe used here is the IND-probe pin on Manta M8P, and the jumper is placed on the two pins beside the probe pins as shown in the image above, to enable 24V supply to the ABL board.

#### Setting up Jumper for CANBUS communication

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/3f0a9d7a-528f-4178-923e-e57a761894fc)


At the top of the two CAN pins, a small jumper is to be placed on the pins that mention '120R' depicting the 120 ohms resistance that is applied on the CAN Low and High communication pins. This is a crucial pin for the setting up of the CAN communication of the motherboard and toolboard.

## Setting up of RP2040 based CAN module/Toolboard

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/60cfe650-99f7-4ce7-b5a9-2989af638ea9)

After the motherboard is powered on, the green LED light will light up, indicating a normal power supply. The VBUS on the right side of the board is the power selection terminal. Only when using USB to supply power to the motherboard or need to supply power through USB, do you need to use the jumper cap to connect VBUS.

Similar to the BTT Manta M8P, the Support communication via CAN or USB. The terminal resistor 120R of CAN can be selected through a jumper cap, and it reserves a CAN expansion interface.

## Wiring and Connections

![Twin Dragon 600 with M8P Wiring](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/5aaddf6d-8737-4d11-959b-e3e86720b1d5)

The overall connections of all the Electrical and Electronic components are present in the image above

  ### BTT Manta M8P Pin connections

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/6e655c8d-638d-4602-86c7-b775c30add44)

## Setting up BTT Manta M8P V2.0 + RPi CM4 + RP2040 based toolboard

After powering on the M8P, the LED on the bottom left corner will light up to indicate normal power supply. The VUSB jumper in the center is for selecting power - it should only be shorted when powering the board via USB or supplying power out via USB.

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/a958c1ba-796f-418f-ada7-2db6b0ebb668)

### Other Initial preparation and setting up jumpers

#### TMC Driver SPI Mode

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/3333b970-bcab-4d4b-b9cb-f18ed82d6cfc)

The first row are the defined pin for the drivers, which are either high or low when shorted or unshorted to establish different mode of communication. The second row are defined with the SPI modes, with the namings of 'MISO', 'CS', 'SCK' and 'MOSI' when read from left to right. Since we use the TMC5160 driver, it specifically operates only on the SPI mode. Insert the jumpers corresponding to its parallel pins only on the 1st and the 2nd row as shown in the image.

#### TMC Driver UART Mode

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/1110018c-07fe-482e-8d79-761831509141)

The given set of pin to short is the CS pin that enables only the uart mode.

#### Driver Voltage selection

For High Voltage selection(48V):

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/bf3a8896-4cff-40da-9098-789842d58acb)

Since the TMC5160 operates only on SPI mode, which is specifically for achieving faster communication and higher speeds, it needs an operating voltage of around 48V. The manta M8P has seperte pins for regular voltage of 24V and high voltage of 48V, that is to be jumped to the common pin of voltage supply to the drivers. We jump the HV pin in the left to the middle pin of supply in order to provide 48V to the drivers, as shown in the image above.

For normal Voltage selection (24V):

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/f2a6d8c0-dbdb-4a7c-89c2-14ec335743cc)

This voltage selection can be used when using a regular TMC2209 on the UART mode

#### Setting up jumper for probe activation

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/b0c7dd86-3f6c-4083-a81b-6fab46435cee)

The pin for probe used here is the IND-probe pin on Manta M8P V2.0, and the jumpers are placed on the two pins beside the probe pins, and other three perpendicular pins to its right, where the top two are to jumped together to activate the probe pin, as shown in the image above, to enable 24V/5V supply to the ABL board. The three columns of the pins starting from the top are 5V, 12V, 24V Respectively.

#### Setting up Jumper for CANBUS communication

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/a540b422-52cb-41cc-b6a8-25c727c4f089)

At the left of the CAN pin, a small jumper is to be placed on the pins that mention '120R' depicting the 120 ohms resistance that is applied on the CAN Low and High communication pins. This is a crucial pin for the setting up of the CAN communication of the motherboard and toolboard.

## Wiring and Connections

![Twin Dragon 600 CM4 M8P V2 0 - Wiring](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/78dbc25f-ff8f-4533-9c9d-a62a0f82dd5e)

The overall connections of all the Electrical and Electronic components are present in the image above

### BTT Manta M8P V2.0 Pin connections

![Twin Dragon 600 with M8P V2 0 Wiring](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/595c8816-327c-440a-9572-f5ab909eb793)


## To setup Raspeberry Pi camera Rev 1.3, interfaced with RPi CM4 and BTT Manta M8P/M5P

In order to interface the Pi camera Rev 1.3 with the RPi CM4 and BTT Manta M8P/M5P, flip the board and check for a CSI1 camera slot, which should look like the image below

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/de2eb324-dc58-4c48-af00-7386afde8c35)

Instructions to attach the camera in BTT Manta M8P V2.0

![image](https://github.com/FracktalWorks/TwinDragon600-Electronics/assets/80109965/1bc509c2-2984-46af-a074-268701a05b0c)


Instructions to attach the camera in BTT Manta M5P

1. Now, boot up the board (including CM4), SSH into the CM4 and open the terminal
2. We will have to download a bin file into the boot folder of the CM4, below is the command to enter into the terminal.

`sudo wget https://datasheets.raspberrypi.com/cmio/dt-blob-cam1.bin -O /boot/dt-blob.bin`

If the above command does not work, try the following command:

`sudo wget https://datasheets.raspberrypi.com/cmio/dt-blob-cam1.bin -O /boot/firmware/dt-blob.bin`

3. Now, in the terminal, enter `sudo raspi-config` and select the option '3 Interface Options    Configure connections to peripherals'. Now select the first option 'P1 Camera      Enable/disable connection to the Raspberry Pi Camera'. A pop-up would appear where it asks to enable the camera. Make sure to select <yes> and exit the portal.

4. Now, in the terminal, type in `sudo nano /boot/config.txt` and make sure the settings are enabled

   `start_x=1
   gpu_mem=128`

   Note: make sure `#camera_auto_select=1` is commented out, or else it will not work.

For more clarifications, check out 'Julia TouchUI documentation' for more settings on Pi-camera





