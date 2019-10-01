# Set up a border router

**We are setting up an 6LoWPAN over Bluetooth interface on Linux. This makes it possible to use a UDP/IP (IPv6) stack on an IoT BLE devices**

## Prerequisites

To complete this guide, you need the following:

- Either a single-board computer such as a Raspberry Pi or a Linux-based PC to use as the border router
- A Linux distribution such as Ubuntu
- Bluetooth <= 4.0 (USB dongle or integrated)

## Step 1. Install a Linux kernel

1. Select your architecture and download the generic kernel image from the 
    [Ubuntu Linux mainline kernel builds](https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11.12/)

    :::info:
    Due to [a bug in RIOT OS](https://github.com/RIOT-OS/RIOT/issues/11147), you need to use an older Linux kernel.
    :::

2. Install the kernel

    ```bash
    sudo dpkg -i linux-image*.deb
    ```

3. Restart your system while holding the SHIFT key until you see the option to select a kernel 
    
4. Select the kernel version 4.11.12

## Step 2. Install the 6LoWPAN dependencies

:::info:
You need to do these steps for every session. So, if you close your session,
for example after a reboot, you have to reinstall the dependencies.
:::

1. Install bluez

    ```bash
    sudo apt-get install -y bluez
    ```

2. Log in as root

    ```bash
    sudo su
    ```

3. Mount the `debugfs` file system

    ```bash
    mount -t debugfs none /sys/kernel/debug
    ```

4. Load the Bluetooth 6LoWPAN Linux module

    ```bash
    modprobe bluetooth_6lowpan
    ```

5. Enable the 6LoWPAN module

    ```bash
    echo 1 > /sys/kernel/debug/bluetooth/6lowpan_enable
    ```

6. Find any available Bluetooth devices

    ```bash
    hciconfig
    ```

7. Reset the device you want to use. Replace the `YOUR_DEVICE_ID` placeholder with the ID of your device.

    ```bash
    hciconfig YOUR_DEVICE_ID reset
    ```

