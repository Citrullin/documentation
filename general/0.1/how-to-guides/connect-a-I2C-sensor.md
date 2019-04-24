# Connect a I2C sensor to your nRF52
**In this guide, we are going to connect a I2C sensor to our nRF52**

## Prerequisites

- nRF52 microcontroller
- I2C sensor

:::info
We use RIOT OS in our examples. If you consider yourself as beginner, 
you should check the [RIOT OS sensor driver list](http://riot-os.org/api/group__drivers__sensors.html), 
before buying any sensor. 
If the sensor you want to use is not in the list, you have to write a driver by yourself.
You can also use another RTOS or library which supports your driver. 
:::

### I2C

I2C is a serial bus. This means that the bits are send sequentially over the wire. 
The I2C bus consists only of two wires. 
SCL is used for the clock and SDA is used to transfer the data.
I2C uses Master-Slave communication. With 7-Bit addressing, 127 addresses are available.
The I2C bus reserves some addresses for the protocol, 
so that you end up with 112 addresses for your sensors.
I2C also has a 10-Bit address space, so that you end up with 1008 addresses for your devices.
Most sensor use the 7-Bit address space, so we recommend to stick to 7-Bit in order to support most sensors.
If you use a sensor more than once on a master, 
you should connect each sensor on a different I2C bus in order to avoid address conflicts.
The I2C protocol does not have any mechanism to resolve address conflicts.
If your device does not have enough I2C buses, 
you can use an I2C switch in order to use your sensors.

### I2C address selection

Most I2C ICs provide a address selection to avoid address conflicts with other I2C ICs.
You should always check the datasheet of your sensor before using it.
Generally it mentions a PIN you have to pull up or low in order to select the I2C address.
    

1. Connect SCL and SDA

    :::info:
    If you consider yourself as beginner, you should start with using a I2C sensor development board.
    If you use the raw IC, you need to pull SCL and SDA to high. [A pull resistor is needed.](https://rheingoldheavy.com/i2c-pull-resistors/)
    The pull up resistor has also an [effect on the square wave.](http://dsscircuits.com/articles/effects-of-varying-i2c-pull-up-resistors)
    You might want to check it before designing a board for a production environment.
    If you use a raw IC, you should understand how the [I2C protocol](http://www.ti.com/lit/an/slva704/slva704.pdf) works before.
    :::
    
    The nRF52 has a feature called [EasyDMA](https://infocenter.nordicsemi.com/index.jsp?topic=%2Fcom.nordic.infocenter.nrf52832.ps.v1.1%2Feasydma.html&cp=3_1_0_9&anchor=easydma).
    The wire protocols are not statically assigned to any PIN. It is [configured with EasyDMA](https://infocenter.nordicsemi.com/index.jsp?topic=%2Fcom.nordic.infocenter.nrf52832.ps.v1.1%2Ftwim.html&cp=3_1_0_32&anchor=concept_scx_f5p_xr).
    RIOT OS assigns P0.26 and P0.27 to the I2C protocol.
        
    | Microcontroller | I2C sensor |
    |-----------------|------------|
    |      P0.26      |     SDA    |
    |      P0.27      |     SCL    |
    
