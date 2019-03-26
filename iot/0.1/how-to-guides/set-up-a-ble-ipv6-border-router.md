# Set up a IPv6 over Bluetooth Low Energy border router
**We are setting up an 6LoWPAN over Bluetooth interface on Linux. 
This makes it possible to use an UDP/IP (IPv6) stack on IoT BLE devices**

## Prerequisites

- Ubuntu (or another linux distro, if you are familiar with it)
- Bluetooth <= 4.0 (USB dongle or integrated)

## Install an older Linux kernel
**Note:** Due to [a bug](https://github.com/RIOT-OS/RIOT/issues/11147), you need to use an older Linux kernel.

### 1. Download your kernel
Select your architecture and download the generic kernel image from the 
[Ubuntu Linux mainline kernel builds.](https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11.12/)

### 2. Install the kernel
```bash
sudo dpkg -i linux-image*.deb
```

### 3. Reboot and select the kernel
Reboot your system and press the SHIFT key while bootup. You can select the older kernel and boot into it.

## Installation

**You need to do this every session. So, if you close your session,
for example after a reboot, you have to do this again.**

### 1. Install bluez
```bash
apt-get install -y bluez
```

### 2. Login as root
```bash
sudo su
```

### 3. Mount debugfs file system
```bash
mount -t debugfs none /sys/kernel/debug
```

### 4. Load Bluetooth 6LoWPAN Linux module
```bash
modprobe bluetooth_6lowpan
```

### 5. Enable the 6LoWPAN module
```bash
echo 1 > /sys/kernel/debug/bluetooth/6lowpan_enable
```

### 6. Get your available Bluetooth devices
```bash
hciconfig
```

### 7. Reset your device
YOUR_DEVICE_ID => e.g. hci0
```bash
hciconfig YOUR_DEVICE_ID reset
```

### 8. Scan for BLE devices
```bash
hcitool lescan
```

### 9. Connect to your BLE devices
**Note:** You can connect multiple devices to your border router.

00:AA:BB:XX:YY:ZZ => Replace with the address of your BLE device
```bash
echo "connect 00:AA:BB:XX:YY:ZZ 1" >> /sys/kernel/debug/bluetooth/6lowpan_control
```