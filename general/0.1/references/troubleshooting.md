# Troubleshooting

**You may find some of these common issues while following these guides.**

## Set up a IPv6 over Bluetooth Low Energy border router

### none already mounted or mount point busy.

If you see this response, ignore it. The file system is probably already mounted.

```bash
mount: /sys/kernel/debug: none already mounted or mount point busy.
```

## Set up an nRF52 microcontroller

### Permission denied

If you see a `permission denied` error while trying to flash your microcontroller, and you're using a DAPLink programmer, create a udev rule by doing the following:

1. Clone the pyOCD repository

  ```bash
  git clone https://github.com/mbedmicro/pyOCD.git
  ```

2. Change into the `pyOCD/udev` directory

  ```bash
  cd pyOCD/udev
  ```

3. [Follow the pyOCD instructions](https://github.com/mbedmicro/pyOCD/tree/master/udev) for creating a udev rule

### arm-none-eabi-gcc version not supported

If you see the `arm-none-eabi-gcc version not supported` message, install the latest version of the toolchain by doing the following:

1. Uninstall the old toolchain packages

  ```bash
  sudo apt remove binutils-arm-none-eabi gcc-arm-none-eabi libnewlib-arm-none-eabi
  ```

2. [Download the latest toolchain from developer.arm.com](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads)

3. Untar the toolchain in your `home` directory. Replace the `$FILENAME` placeholder with the name of the file that you downloaded

  ```bash
  tar -xjvf $FILENAME
  ```

4. Add the toolchain to your path. Replace the `$PATHTOFILE` placeholder with the path to your untarred toolchain

  ```bash
  echo "export PATH=$PATH:/home/$PATHTOFILE/bin/" >> ~/.bashrc
  ```

5. Close the terminal window, and open a new one

Now, you should have a supported version of the toolchain

### Recipe for target 'flash' failed

When you use a J-Link OB clone for the first time the flashing might fail. 
Don't be surprised to receive a message like this

```bash
recipe for target 'flash' failed
make: *** [flash] Error 1
```

If the J-Link OB clone was upgraded before, everything works fine. After the upgrade, you can execute the flash command a second time and the flashing works like expected. The upgrade which leads to the temporary error looks
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
