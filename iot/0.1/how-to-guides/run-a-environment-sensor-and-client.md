# Run a nRF52 sensor and client
**In this guide we create a professional 6LoWPAN IoT sensor node setup. 
The sensor gets an individual IPv6 address. Therefore, we can send UDP/IP packets to this sensor.**

## Prerequisites

- [Configured 6LoWPAN network](set-up-a-bluetooth-star-network.md)
- [Installed nRF toolchain](root://iot/0.1/how-to-guides/set-up-nrf-toolchain.md)
- [Installed Golang](https://golang.org/doc/install)
- DHT11- or DHT22-sensor
- nRF52832

1. Connect the environment sensor to your nRF52

2. Flash the env sensor firmware to your microcontroller
    
    If you haven't done this already, you need to flash the env sensor firmware.
    
    clone the forked RIOT OS repo
    ```bash
    git clone https://github.com/iota-community/BLE-environment-sensor.git
    ```
    
    ```bash
    cd BLE-environment-sensor/examples/env_sensor_network/
    ```
    
    USB_PORT => the USB port your UART-to-USB dongle is connected to. e.g. /dev/ttyUSB0
    ```bash
    BOARD=nrf52dk PORT=USB_PORT make flash term
    ```
    
3. Start the environment server
    
    You need to execute the following command in the serial console on your microcontroller
    ```bash
    server start
    ```
    
4. Clone the server client

    ```bash
    git clone https://github.com/iota-community/BLE-environment-sensor-client.git $GOPATH/src/github.com/citrullin/udp_client
    ```
    
5. Run the client application

    ```bash
    cd $GOPATH/src/github.com/citrullin/udp_client && go run client.go
    ```