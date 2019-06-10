# Troubleshooting

## This kernel requires an x86-64 CPU

Make sure that you selected a 64-bit version of Ubuntu in VirtualBox.

## When in doubt

Try rebooting your computer to see if that resolves any issues.

## Setup SBC

### Can you successfully login to your device and just some characters are weird? 

If you can read the messages while system boot and just some characters are weird, this is not abnormal. 
Just continue using it. You should switch to an SSH terminal as fast as possible 
due to some problems with the serial terminal.

### Have you checked your baud rate? 
Take a look into the documentation of your device or ask in some forum. 
It might be the case that your device is not configured correctly. Just try common baud rates.

### Are you using a standard USB charger or the USB-port of a PC to power up your device?

You might want to try a more powerful power supply. Usually the powerful ones have a fixed Micro-USB cable.
Make sure to buy one with at least 2A. Better: 3A.

## Set up a IPv6 over Bluetooth Low Energy border router

### none already mounted or mount point busy.

When you get this response
```bash
mount: /sys/kernel/debug: none already mounted or mount point busy.
```
just continue with the guide. The file system is probably already mounted.

## Flash a nRF5x microcontroller

###  recipe for target 'flash' failed

When you use a J-Link OB clone for the first time the flashing might fail. 
Don't be surprised to receive a message like this

```bash
recipe for target 'flash' failed
make: *** [flash] Error 1
```

If the J-Link OB clone was upgraded before, everything works fine. After the upgrade, you can execute the flash
command a second time and the flashing works like expected. The upgrade which leads to the temporary error looks
like this:

```bash
### Flashing Target ###
### Flashing at base address 0x0 with offset 0 ###
SEGGER J-Link Commander V6.44 (Compiled Mar  1 2019 17:36:52)
DLL version V6.44, compiled Mar  1 2019 17:36:42

J-Link Commander will now exit on Error

J-Link Command File read successfully.
Processing script file...

J-Link connection not established yet but required for command.
Connecting to J-Link via USB...Updating firmware:  J-Link ARM-OB STM32 compiled Aug 22 2012 19:52:04
Replacing firmware: J-Link ARM-OB STM32 compiled Jun 30 2009 11:14:15
  ... Firmware update successful. CRC=BEA0
Waiting for new firmware to boot
FAILED: Communication timed out: Requested 2 bytes, received 0 bytes !
EMU_GetFirmwareString: Insufficient data read when trying to read the string length.

Script processing completed.

```
