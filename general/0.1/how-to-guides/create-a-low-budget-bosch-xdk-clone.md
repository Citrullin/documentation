# Create a low-budget sensor application

**In this guide, we create a low-budget sensor application that has similar features to the Bosch XDK.**

## Prerequisites

- [Set up an nRF52 microcontroller](../how-to-guides/set-up-nrf52-microcontroller.md)
- [Connect a BME/BMP 280 sensor to the microcontroller](../how-to-guides/connect-bosch-bme-280-bmp-280.md)
- **Optional:** [Connect a TSL2561 (Lux sensor), VEML6070 (UV sensor)](../how-to-guides/connect-a-I2C-sensor.md) or [other supported I2C sensor](http://riot-os.org/api/group__drivers__sensors.html) to the microcontroller

---

1. Change into the `BLE-environment-sensor/examples/saul` directory

    ```bash
    cd BLE-environment-sensor/examples/saul
    ```

2. In the `Makefile` file, add `USEMODULE += bmx280` under `USEMODULE += ps` so that the driver for the BME/BMP 280 sensor can be compiled into your application

    :::info:
    All driver module names for the pattern `USEMODULE += DRIVER_NAME` are in the `drivers` directory.
    :::  
    
    :::info:
    If you're using the optional TSL2561 and VEML6070 sensors, also add `USEMODULE += tsl2561` and `USEMODULE += veml6070` to the file.
    :::
    
3. Compile and flash the operating system and application. Replace the `$BOARD` AND `$USB_PORT` placeholders with the name of your board AND the path to your USB-to-UART connector such as `/dev/ttyUSB0` 
    
    ```bash
    BOARD=BOARD PORT=USB_PORT make flash term
    ```

    :::info:
    See the RIOT documentation to [find the name of your board](https://api.riot-os.org/group__boards.html).
    :::

4. Use the RIOT OS [hardware abstraction layer (HAL)](https://en.wikipedia.org/wiki/Hardware_abstraction) ([SAUL](https://riot-os.org/api/group__drivers__saul.html)) to find a list of all available sensors

    :::info:
    You can also access the sensor by its [SAUL device class](https://riot-os.org/api/group__drivers__saul.html#ga425be5f49e9c31d8d13d53190a3e7bc2)
    :::
    
    ```bash
    saul
    ```
    
    You should see a list of all available sensors. For example:

    ```bash
    ID	Class		Name
    #0	ACT_SWITCH	LED 1
    #1	ACT_SWITCH	LED 2
    #2	ACT_SWITCH	LED 3
    #3	ACT_SWITCH	LED 4
    #4	SENSE_BTN	Button 1
    #5	SENSE_BTN	Button 2
    #6	SENSE_BTN	Button 3
    #7	SENSE_BTN	Button 4
    #8	SENSE_TEMP	NRF_TEMP
    #9	SENSE_TEMP	bme280
    #10	SENSE_PRESS	bme280
    #11	SENSE_HUM	bme280
    #12	SENSE_LIGHT	tsl2561
    #13	SENSE_UV	veml6070
    ```
    
5. To read the data from a particular sensor, do `saul read` followed by an ID. To read the data from all sensors, do `saul read all`.

## Next steps

You should read sensor data from a shell session only while debugging.

For a real application, [set up a sensor server](../how-to-guides/run-a-environment-sensor-and-client.md) that allows clients to connect to it and read its data. 
