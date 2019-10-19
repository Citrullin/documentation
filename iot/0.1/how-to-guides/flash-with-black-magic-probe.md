# Flash microcontroller with black magic probe

**In this guide, you learn how to flash a microcontroller with a black magic probe**

## Prerequisites

- Linux operating system
- DuPont cables
- [Black Magic Probe](https://github.com/blacksphere/blackmagic/wiki) or [Bluepill/Blackpill (STM32F1) with ST-LinkV2](https://github.com/blacksphere/blackmagic/tree/master/src/platforms/stlink)
- nRF52 microcontroller development board

1. Optional: [Flash the BMP (Black magic probe) app onto your Bluepill/Blackpill.](https://buger.dread.cz/black-magic-probe-bmp-on-bluepill-stm32f103c8-minimum-system-development-board.html)

2. Install Python 3

```bash
sudo apt-get install python3
```

5. Go into your application folder

`$RIOT_base` is the base where you cloned the git repository into.

Example:
```bash
cd $RIOT_base/examples/hello_world
```

6. Install python requirements

```bash
pip install humanize pygdbmi pyserial progressbar
```

7. Build application

```bash
BOARD=nrf52dk make 
```

8. Erase flash storage of the microcontroller

```bash
../../dist/tools/bmp/bmp.py --connect-srst erase
```

9. Connect to microcontroller shell

`$RIOT_base` is the based where you cloned the repository into.

Open another terminal and execute the following commands:
```bash
cd $RIOT_base
./dist/tools/bmp/bmp.py --connect-srst term
```

The response should look like the following:

```bash
picocom v2.2

port is        : /dev/ttyACM5
flowcontrol    : none
baudrate is    : 115200
parity is      : none
databits are   : 8
stopbits are   : 1
escape is      : C-a
local echo is  : no
noinit is      : no
noreset is     : no
nolock is      : yes
send_cmd is    : sz -vv
receive_cmd is : rz -vv -E
imap is        : lfcrlf,
omap is        : 
emap is        : crcrlf,delbs,

Type [C-a] [C-h] to see available commands

Terminal ready
```

9. Flash your application onto the microcontroller

Replace $APPLICATION_NAME with the name of your application. You can find the name of your application in the Makefile.
Example:
```
APPLICATION = env_sensor_network
```

```bash
../../dist/tools/bmp/bmp.py --connect-srst flash bin/nrf52dk/$APPLICATION_NAME.elf 
```

