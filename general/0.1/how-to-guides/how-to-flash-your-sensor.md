# How to flash your sensor device
**In this guide, we are going to explain step by step how to flash your sensor device**

## The differences: Firmware, OS and RTOS

Microcontroller work different compared to normal PCs or SBCs. 
On a normal PC/SBC, the operating system is located on some kind of storage system. (HDD, SDD, SD Card, eMMC)
Before the system can boot into the OS on your storage, the system has to able to communicate with this storage system.
This is where the [firmware](https://en.wikipedia.org/wiki/Firmware#Personal_computers) comes into play.
The firmware has the basic driver for this communication.
Before your system runs the OS, it runs this firmware. The firmware tells the system how to start into your OS. 
There are more components than just the storage system, but it gives a general understanding why a firmware exist.

Microcontrollers on the other hand only run the firmware. 
When we speak about an OS in context of a Microcontroller, 
we speak about [RTOS (realtime operating-systems)](https://en.wikipedia.org/wiki/Real-time_operating_system).
In comparison to your OS on your PC/SBC, the RTOS is smaller and has to meet specific deadline requirements.
The RTOS is also embedded into the firmware. 
When we write an application on our RTOS, we combine everything into one binary and flash it onto the flash memory of
our microcontroller. The microcontroller is able to run the compiled code directly.

## How to flash/program the microcontroller?

In order to get our binary onto our microcontroller, we have to flash it onto the flash memory. 
There are generally two interfaces for flashing your microcontroller. 
[Serial Wire Debug](http://www.ti.com/lit/wp/spmy004/spmy004.pdf) and [JTAG](https://en.wikipedia.org/wiki/JTAG).
Both use the same protocol, but have different pin counts. 
We use a device called programmer in order to flash our binary directly to the microcontroller.
J-Link is one of the most famous general programmers. You are able to program most microcontroller with the J-Link.
There are also other programmer specific for microcontroller produced by one company. 
One example is the [STLinkV2](https://www.st.com/en/development-tools/st-link-v2.html), 
which is used to program micrcontroller produced by [STMicroelectronics](https://de.wikipedia.org/wiki/STMicroelectronics).

Some microcontroller, such as the Arduino ones, use something called bootloader. 
The bootloader works similar as the firmware for an OS on your PC/SBC. 
The bootloader adds some logic to the microcontroller, so that you are able to program the microcontroller via USB.
This is more use-friendly, since you don't need additional hardware to start with microcontroller programming.
The downside of using a bootloader is wasted space on our flash memory. 
The bootloader adds logic we actually do not need to run our application. 

In our tutorials we will always use tools to abstract the interaction with the microcontroller. 
You do not need to know the details of the JTAG protocol.
A general understanding of the architecture is good enough. 
 