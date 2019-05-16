# Set up a nRF52 microcontroller
**In this guide, we are going to set up a nRF52 development board**

## Prerequisites

- nRF52832 development board
- Linux based PC

:::info:
You have a lot of options for your nRF52832 development board.
To name a few options:
- nRF52832 breakout board by Sparkfun @ ~20 USD
- nRF52 DK @ ~40 USD
- nRF52832-MDK @ ~30 USD
- nRF52832 USB Dongle @ ~10 USB
- chinese nRF52832 module + nrf52832 Minimum Test Board @ ~10 USD
:::

- J-Link, J-Link OB clone or DAPLink

:::info
Some development boards have an integrated J-Link or DAPLink. If you have one of these boards, you don't need an additional
J-Link. Check the datasheet of your development board before.
:::

- USB-to-UART adapter
    
1. Optional: Solder JTAG pins and GPIO pins

    :::info:
    Soldering the pins on some boards is quite hard. You should keep this in mind before you buy a development board.
    Check that the development baord does not have half pin holes.
    :::

    This is not needed for every development board. Your board might has all necessary pins already soldered.
    If all pins are soldered, you can skip this part.
    
    **nRF52832 USB dongle**
    ![nRF52832 USB dongle soldered pins](../images/nrf52832_usb_dongle_soldered_pins.png)
    
    **chinese nRF52832 module + nrf52832 Minimum Test Board**
    ![chinese nRF52832 minimum test board soldered](../images/nrf52_cheap_board.png)
    
2. [Connect your J-Link/DAPLink and USB-to-UART adapter](connect-nrf-jlink-serial-console.md)

    :::info
    If your board has an integrated J-Link/DAPLink, you don't need to connect the J-Link to your board. 
    The J-Link/DAPLink already exposes an USB-Port. Check the datasheet of your board before.
    :::


    
    