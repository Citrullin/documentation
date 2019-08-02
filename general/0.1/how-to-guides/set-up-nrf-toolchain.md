# Set up nordic nRF toolchain
**In this, we are going to set up the Nordic nRF toolchain, in order to be able to program and flash our microcontroller**

## Prerequisites

- Linux based PC
:::info:
Your microcontroller needs to be connected to this PC.
:::

1. Install git

    [Follow the github guide](https://help.github.com/en/articles/set-up-git)

2. Install ARM Toolchain

    [Follow this guide on gnu mcu eclipse](https://gnu-mcu-eclipse.github.io/toolchain/arm/install/#gnulinux-1)

3. Install the programmer tools
 
   Option 1: J-Link or J-Link OB

   [Follow this guide on gnu mcu eclipse](https://gnu-mcu-eclipse.github.io/debug/jlink/install/)
    
   Option 2: DAPLink
   
   Execute the following command:
   ```pip install pyocd --user -U```

4. Install OpenOCD

    [Follow the guide on the RIOT github page](https://github.com/RIOT-OS/RIOT/wiki/OpenOCD)

5. Install python

    ```bash
    sudo apt-get install -y python3-all
    ```

6. Install python-pip

    ```bash
    sudo apt-get install -y python3-pip
    ```