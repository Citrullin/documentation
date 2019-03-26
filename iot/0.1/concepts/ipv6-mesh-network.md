# IPv6 mesh network
**This document contains some definitions about IoT 6LoWPAN mesh networks**

## Naming convention

### IEEE 802.15.4

[IEEE 802.15.4](https://standards.ieee.org/standard/802_15_4-2015.html) is the PHY and MAC layer for our 6LoWPAN network. 
The Direct Sequence Spread Spectrum modulation used in IEEE 802.15.4 
interferes less with other protocol on the same frequency. 

### 6LoWPAN

6LoWPAN stands for "IPv6 over Low power Wireless Personal Area Network" 
and describes a protocol which makes IPv6 packets more efficient and therefore usable for constraint devices.
It uses for example header compression to reduce the size of local IPv6 addresses.
IPv6 requires a MTU of at least 1280 bytes, but the IEEE 802.15.4 protocol has only a packet size of 127 bytes.
The 6LoWPAN layer uses transparent packet fragmentation to combine the IEEE 802.15.4 packets.
Keep in mind: If one of the IEEE 802.15.4 fragmentation is lost, the complete 6LoWPAN packet is lost.
Therefore, we should always keep the packets as small as possible. 
The standard is defined in 
[RFC 8025](https://datatracker.ietf.org/doc/rfc8025/), 
[RFC 6775](https://datatracker.ietf.org/doc/rfc6775/), 
[RFC 6282](https://datatracker.ietf.org/doc/rfc6282/), 
[RFC 8066](https://datatracker.ietf.org/doc/rfc8066/) 

### IPv6 over Bluetooth Low Energy

The IPv6 over Bluetooth Low Energy protocol uses 6LoWPAN techniques to enable IPv6 packets over
Bluetooth Low Energy. The standard is described in [RFC7668](https://datatracker.ietf.org/doc/rfc7668/). 
The standard utilizes the 
[IPSP characteristics](https://www.bluetooth.org/docman/handlers/DownloadDoc.ashx?doc_id=296307) in Bluetooth >= 4.1.
The complete IP standard on Bluetooth is defined in the [Bluetooth 4.2 specification](https://www.bluetooth.org/DocMan/handlers/DownloadDoc.ashx?doc_id=286439).

### RPL

RPL is a routing protocol used for 6LoWPAN. 
The standard is defined in [RFC 6550](https://datatracker.ietf.org/doc/rfc6550/).

### Border Router

Border router are connecting the 6LoWPAN with an IPv6 network. To keep it simple:
The Border router connects our IoT mesh network to the Internet. 
The Border router is not necessarily connecting the mesh 6LoWPAN directly to the Internet.
The router can also be connected to a private or public Wifi.

## Network stack

### IPv6 over Bluetooth Low Energy

