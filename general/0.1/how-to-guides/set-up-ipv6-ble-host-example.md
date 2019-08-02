# Set up an IPv6 Bluetooth Low energy host example application
**In this guide, we are going to set up our BLE host example**

## Prerequisites

:::info:
Due to a bug in RIOT OS, the nRF52823 is only supported at the moment. An implementation for state-of-the-art hardware,
such as the nRF52840 is in progress. We will update the documentation when this implementation is ready to use.
:::

- nRF52823
- Installed [nRF toolchain](set-up-nrf-toolchain.md)
- Connected [serial console and J-Link](connect-nrf-jlink-serial-console.md)
- Linux based PC (the machine which is connected to your Microcontroller.)

1. Clone the forked RIOT OS repository

    :::info:
    We forked the RIOT OS repository and added some packages and examples which are currently not in the mainline kernel.
    :::
    
    Clone the forked RIOT OS repository on your PC. 
    ```bash
    git clone https://github.com/iota-community/BLE-environment-sensor.git
    ```

2. Flash the IPv6 Bluetooth server example

    :::info:
    This is only an example application. You can replace the server with your own implementation, if you want to.
    The server logic is written in BLE-environment-sensor/examples/env_sensor_network/server.c
    Get a general understand about the [flashing process](how-to-flash-your-sensor.md).
    :::

    Go to the example directory
    ```bash
    cd BLE-environment-sensor/examples/env_sensor_network/
    ```
    
    Flash the example and open the terminal
    YOUR_BOARD: [Check the RIOT OS API wiki](http://www.riot-os.org/api/group__boards.html) 
    to find the name for your board.
    e.g. nrf52dk
    
    USB_PORT => the USB port your UART-to-USB dongle is connected to. e.g. /dev/ttyUSB0
    
    ```bash
    BOARD=YOUR_BOARD PORT=/dev/ttyUSB0 make flash term
    ```
    You can check all commands with ``help``. RIOT also shows you all running processes with ``ps``