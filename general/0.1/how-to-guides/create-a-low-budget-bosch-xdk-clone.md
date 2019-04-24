# Create a low budget sensor node like the Bosch XDK
**In thise guide, we are going to create a low budget sensor node which has similar features as the Bosch XDK**

## Prerequisites

- [nRF52832](set-up-nrf52-microcontroller.md)
- [Connected BME/BMP 280 sensor](connect-bosch-bme-280-bmp-280.md)
- [Optional: Connected TSL2561 (Lux sensor), VEML6070 (UV sensor)](connect-a-I2C-sensor.md) 
or [other supported I2C sensors](http://riot-os.org/api/group__drivers__sensors.html)

:::info:
You might want to read our ["Run a nRF52 sensor and client"](../../../blueprints/0.1/environment-sensor/run-a-environment-sensor-and-client.md)
in order to be able to use this sensor node in an advanced fashion
:::

1. Clone the forked RIOT OS

```bash
git clone https://github.com/iota-community/BLE-environment-sensor.git
```

2. Go into examples/saul

```bash
cd BLE-environment-sensor/examples/saul
```

3. Add the driver module(s) to the Makefile

:::info:
RIOT OS is a [microkernel operation system](https://wiki.osdev.org/Microkernel).
The modulation helps to keep the operation as clean as possible.
Only the needed functionality will be compiled into our app binary.
This is beneficial for microcontroller due to a general lower footprint.
All DRIVER_NAMES for the pattern ```USEMODULE += DRIVER_NAME``` can be found in the directory
drivers. Some driver have a x variable in their namings. 
For example the BME/BMP 280 driver is named bmx280.
::: 

Add ```USEMODULE += bmx280``` to the Makefile. Right under ```USEMODULE += ps```
This adds the driver module into the make process and compiles it into your application.

If you want to use the TSL2561 as well, you also need to add ```USEMODULE += tsl2561```.
For the VEML6070, use ```USEMODULE += veml6070```.

4. Compile and flash the OS and application

USB_PORT = the usb port your uart-to-usb adapter is connected to. for example: /dev/ttyUSB1

```bash
BOARD=nrf52dk PORT=USB_PORT make flash term

```

5. Read the sensor data

:::info:
RIOT OS has an [HAL](https://en.wikipedia.org/wiki/Hardware_abstraction) (Hardware abstraction layer) 
called [SAUL](https://riot-os.org/api/group__drivers__saul.html) (Sensor Actuator Uber Layer)
You can access the sensor by its generic SAUL type. ([sensor.c](https://github.com/iota-community/BLE-environment-sensor/commit/dbd09e190e5f231a3bd575d5137d5ac03d3c563a#diff-65a5e0b8b7c3c44ad2827b59684b75ecR16) contains an example)
:::

We are going to use the shell to access the sensor data.

execute the following command in the shell:
```bash
saul
```

This returns a list of all available sensor. For example:
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

By executing  ```saul read ID``` you can read the current sensor value. 
If you want to read all sensor, just execute ```saul read all```.

The shell should only be used for debugging. 
Follow the guide ["Run a nRF52 sensor and client"](../../../blueprints/0.1/environment-sensor/run-a-environment-sensor-and-client.md) to get a complete sensor server and client running.

