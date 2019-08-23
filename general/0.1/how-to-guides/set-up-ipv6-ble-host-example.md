# Set up an IPv6 sensor server

**In this guide, we are going to set up a sensor server that accepts UDP packages on port 51037.**

:::info:
Due to a bug in RIOT OS, only the nRF52832 is supported at the moment. An implementation for state-of-the-art hardware such as the nRF52840 is in progress.
:::

## Prerequisites

- [Set up an nRF52832 microcontroller](../how-to-guides/set-up-nrf52-microcontroller.md)
- [Connect a BME/BMP 280 sensor to the microcontroller](../how-to-guides/connect-bosch-bme-280-bmp-280.md)
- Linux-based PC that's connected to your microcontroller

---

1. Change into the `BLE-environment-sensor/examples/env_sensor_network` directory

    ```bash
    cd BLE-environment-sensor/examples/env_sensor_network/
    ```
    
2. Flash the example onto the microcontroller. Replace the `$BOARD` AND `$USB_PORT` placeholders with the name of your board AND the path to your USB-to-UART connector such as `/dev/ttyUSB0` 
    
    ```bash
    BOARD=BOARD PORT=/dev/ttyUSB0 make flash term
    ```

    :::info:
    See the RIOT documentation to [find the name of your board](https://api.riot-os.org/group__boards.html).
    :::

    :::info:
    This is an example application. You can edit the `BLE-environment-sensor/examples/env_sensor_network/server.c` and `BLE-environment-sensor/examples/env_sensor_network/sensor.c` files to support different sensors to the BME/BMP 280.
    :::

If everything went well, you should see no errors, and if you do `help`, you should see a list of available commands.

To see a list of all running processes, do `ps`.

