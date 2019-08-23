# Set up an nRF52 microcontroller

**Some nRF52 series microcontrollers do not have an integrated programmer or soldered pins. In this case, you need to solder the pins, In this guide, we set up a nRF52 development board that doesn't have an integrated programmer or soldered pins.**

## Prerequisites

- nRF52 microcontroller
- Linux-based PC
- An internal or external [programmer](https://www.engineersgarage.com/tutorials/microcontroller-programmer-burner): J-Link, J-Link on-board clone or DAPLink
- A USB-to-UART connector

:::info
Some development boards have an integrated programmer. If you have one of these boards, you don't need an additional programmer.

To find out if your board has an integrated programmer, see its datasheet.
:::

## Step 1. Set up the hardware for your microcontroller
    
1. If the pins on your microcontroller aren't soldered onto the board, solder them.

    :::info:
    Soldering the pins is difficult on some boards. You should keep this in mind before you buy a development board.
    :::
    
    **nRF52832 USB dongle**
    ![nRF52832 USB dongle soldered pins](../images/nrf52832_usb_dongle_soldered_pins.png)
    
    **chinese nRF52832 module + nrf52832 Minimum Test Board**
    ![chinese nRF52832 minimum test board soldered](../images/nrf52_cheap_board.png)
    
2. **Optional:** [Connect your programmer and USB-to-UART adapter](../how-to-guides/connect-to-serial-interface.md)

    :::info
    If your board has an integrated programmer, you don't need to connect the J-Link to your board. 
    The J-Link/DAPLink already exposes a USB port. Check the datasheet of your board for more information.
    :::

## Step 2. Set up the software on your PC

To program and flash a microcontroller, you need a Linux-based PC that has the necessary tools, which are known as a toolchain.

1. [Install Git](https://help.github.com/en/articles/set-up-git)

2. [Install the ARM toolchain](https://gnu-mcu-eclipse.github.io/toolchain/arm/install/#gnulinux-1)

3. [Install OpenOCD](https://github.com/RIOT-OS/RIOT/wiki/OpenOCD)

4. Install Python

    ```bash
    sudo apt-get install -y python3-all
    ```

5. Install PIP

    ```bash
    sudo apt-get install -y python-pip3
    ```

6. Install the programmer toolchain, depending on the programmer that you're using
 
   **Option 1:** [Install the J-Link or J-Link OB tools](https://gnu-mcu-eclipse.github.io/debug/jlink/install/)
    
   **Option 2:** [Install the DAPLink tools](https://github.com/mbedmicro/pyOCD#installing)

7. Clone the forked RIOT OS repository

    :::info:
    RIOT OS is a modular [microkernel operating system](https://wiki.osdev.org/Microkernel).
    The modularity helps keep the operating system as small as possible by allowing you to compile only the modules that are essential for your application. This feature is beneficial for microcontrollers because they often have a small amount of available memory space.
    :::

    ```bash
    git clone https://github.com/iota-community/BLE-environment-sensor.git
    ```

8. Change into the `examples/hello-world` directory

    ```bash
    cd examples/hello-world
    ```

9. To make sure that everything is working, flash the hello world example to your microcontroller. Replace the `$BOARD` AND `$USB_PORT` placeholders with the name of your board AND the path to your USB-to-UART connector such as `/dev/ttyUSB0` 

    ```bash
     BOARD=BOARD PORT=/dev/ttyUSB0 make flash term
     ```

     :::info:
    See the RIOT documentation to [find the name of your board](https://api.riot-os.org/group__boards.html).
    :::

## Next steps

Follow one of the following microcontroller-based guides

- [Create a low-budget Bosch XDK](../how-to-guides/create-a-low-budget-bosch-xdk-clone.md)
- [Run an environment sensor server](../how-to-guides/run-a-environment-sensor-and-client.md)
- [Run an environment-to-Tangle app](../how-to-guides/run-an-environment-to-tangle-app.md)



  


    
    