# Set up an IPv6 Bluetooth Low energy host

## Prerequisites

:::info:
Due to a bug in RIOT OS, the nRF52823 is only supported at the moment. An implementation for state-of-the-art hardware,
such as the nRF52840 is in progress. We will update the documentation when this implementation is ready to use.
:::

- nRF52823
- Installed [nRF toolchain](set-up-nrf-toolchain.md)
- Connected [serial console and J-Link](connect-nrf-jlink-serial-console.md)
- Linux based host-system (the machine which is connected to your Microcontroller)

1. Clone the forked RIOT OS repository

    :::info:
    We forked the RIOT OS repository and added some packages and examples which are currently not in the mainline kernel.
    :::
    Clone the forked RIOT OS repository on your host-system. 
    ```bash
    git clone https://github.com/iota-community/BLE-environment-sensor.git
    ```

2. Flash the IPv6 Bluetooth example

    :::info:
    It is not necessary to use the server application. You can also use another one. 
    It is only necessary to include the network layer in order to to be able to connect to the device.
    All examples with gnrc_ should also work and provide all network functionality. 
    You might want to try out the gnrc_minimal example in order to abe to ping the device.
    :::

    Go to the example directory
    ```bash
    cd BLE-environment-sensor/examples/env_sensor_network/
    ```
    
    Flash the example and open the terminal
    ```bash
    BOARD=nrf52dk PORT=/dev/ttyUSB0 make flash term
    ```
    You can check all commands with ``help``. RIOT also shows you all running processes with ``ps``