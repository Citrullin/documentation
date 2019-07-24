# Run a nRF52 sensor and client
**In this guide we create a professional 6LoWPAN IoT sensor node setup. 
The sensor gets an individual IPv6 address. Therefore, we can send UDP/IP packets to this sensor.**

## Prerequisites

- [Configured 6LoWPAN network](../../../general/0.1/how-to-guides/set-up-a-bluetooth-star-network.md)
- [Installed nRF toolchain](../../../general/0.1/how-to-guides/set-up-nrf-toolchain.md)
- [Installed Golang toolchain](https://golang.org/doc/install)
- DHT11- or DHT22-sensor
- nRF52832

## Architecture

![Environment sensor architecture](../architecture_visualisation.png)

### Sensor

The environment sensor runs a server application. This server application uses the request-response message pattern.
The example server application opens an UDP port and waits for incoming requests on this port. 
The response will be sent back to the client on the same port the client sends a message.
One example: 
If the client (SBC or PC) sends an UDP packet on port 90 (outgoing-port at the SBC) to port 51037 (incoming-port on the sensor), 
the sensor will send the response to port 90 (SBC or PC).
Therefore incoming- and outgoing-port are the same on each device. 
In my example the sensor is receiving and sending the UDP packets on port 51037, 
while the client is receiving and sending packets on port 90.
Technically speaking both devices run a server in order to receive UDP packets. 
On an abstract level this design is still a request-response message pattern, 
because the sensor only responds with UDP packets when it received a correct message before.
This complex design is only necessary to keep the traffic as small as possible.
UDP is a connection-less protocol. It is, compared to TCP, more efficient and more resilient.
This is exactly what we need in a lossy networks with small bandwidth. 
We might lose some packets, so we might need to send one message more than once. 
If we would use TCP, this would lead to a big overhead, due to the connection based networking.

## How to run the sensor server and client

1. Connect the DHT sensor to your nRF52
    
2. Start the server on your microcontroller
    
    You need to execute the following command in the serial console on your microcontroller.
    The shell terminal of your microcontroller is opened in the terminal where you executed ```make flash term```
    
    Execute the following command:
    
    ```bash
    server start
    ```
    
3. Clone the server client

    ```bash
    git clone https://github.com/iota-community/BLE-environment-sensor-client.git $GOPATH/src/github.com/citrullin/udp_client
    ```
    
4. Run the client application

    ```bash
    cd $GOPATH/src/github.com/citrullin/udp_client && go run client.go
    ```