# Create a simple Bluetooth star network (6LoWPAN network)
**We are going to set up a a Bluetooth star network using state of the art IoT industry standards.**

We are going to use 6LoWPAN for our Bluetooth network.
Before we get deeper into the topic, you should first read the [IPv6 mesh network concepts](../concepts/ipv6-mesh-network.md).


## Prerequisites

- Linux based PC/SBC (Might be a Raspberry Pi or similar)
- Installed [nRF toolchain](set-up-nrf-toolchain.md)
- Configured [BLE Border router](set-up-a-ble-ipv6-border-router.md)
- Configured and flashed [IPv6 BLE host(s)](set-up-ipv6-ble-host.md) node


1. Scan for BLE devices on your border router

    You need to scan for Bluetooth devices on your border router.
    ```bash
    hcitool lescan
    ```
    You can also verify the address with executing the following command on the serial console on your microcontroller
    ```bash
    ifconfig
    ```
    
    The Long HWaddr is the Bluetooth MAC address. It must be the same as the MAC address in the hcitool.
    

2. Connect your BLE host to your BLE border router

    :::info:
    You can connect multiple devices to your border router.
    :::
    
    00:AA:BB:XX:YY:ZZ => Replace with the address of your BLE device
    
    ```bash
    echo "connect 00:AA:BB:XX:YY:ZZ 1" >> /sys/kernel/debug/bluetooth/6lowpan_control
    ``` 
