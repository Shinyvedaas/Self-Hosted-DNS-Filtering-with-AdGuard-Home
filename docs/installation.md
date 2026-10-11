# Installation Guide

## 1. Operating System Preparation

### Objective

Prepare the Raspberry Pi 5 to run AdGuard Home as a dedicated DNS filtering server.

### Hardware

- Raspberry Pi 5
- microSD card or compatible SSD ( 16 or 32 gb recommended )
- Wi-Fi network or Ethernet ( Ethernet recommended )
- Computer running Raspberry Pi Imager

### Operating System

- Distribution: Raspberry Pi OS Lite (64-bit)
- Device hostname: `adguard-pi`
- Network connection: Wi-Fi or Ethernet
- Time zone: `Europe/Paris`
- Remote administration: SSH enabled

### Installation Procedure

1. Download Raspberry Pi Imager from the [official Raspberry Pi website](https://www.raspberrypi.com/software/).
2. Select Raspberry Pi 5 as the target device.
3. Select Raspberry Pi OS Lite (64-bit).
4. Select the intended storage device.
5. Configure the hostname, username, password, Wi-Fi credentials, wireless LAN country, time zone, and SSH access.
6. Write the image and wait for verification to finish.
7. Insert the storage device into the Raspberry Pi 5 and power it on.

### Security Considerations

- Use a strong, unique password for the administrative account.
- Enable SSH for administration from the local network.
- Do not expose SSH directly to the public internet.
- Never commit passwords or Wi-Fi credentials to the repository.

### Verification Checklist

- [✓] OS image written successfully
- [✓] Image verification completed
- [✓] Raspberry Pi boots successfully
- [✓] Wi-Fi connection established
- [✓] SSH access verified


## 2. Initial Access and System Verification

### Objective

Verify that the Raspberry Pi 5 is accessible remotely over the local Wi-Fi network and is ready for application deployment.

### Access Method

- Client: Any OS
- Remote access: SSH
- Server: Raspberry Pi 5

### Verification Procedure

The following commands are used to inspect the operating system, CPU architecture, hostname, network interfaces, IP addresses, and SSH service status.

```bash
cat /etc/os-release
uname -m
hostname
hostname -I
ip -br addr
systemctl is-active ssh
```

### Verification Results

- [✓] Operating system identified
- [✓] CPU architecture confirmed
- [✓] Hostname confirmed
- [✓] Local IP address identified
- [✓] SSH service confirmed active


## 3. Network Configuration and Stable IP Address

### Objective

Ensure the Raspberry Pi remains reachable at a consistent local IP address for reliable DNS service.

### Configuration Method

DHCP reservation on the home router.

### Procedure

1. Identify the Raspberry Pi's IPv4 address, Wi-Fi interface, and default gateway.
2. Identify the Wi-Fi interface's MAC address.
3. Create a DHCP reservation in the router's administration interface.
4. Associate the reservation with the Raspberry Pi's Wi-Fi MAC address.
5. Reconnect the device or renew its DHCP lease if necessary.
6. Verify that the Raspberry Pi retains the reserved address.

### Verification

- [✓] Default gateway identified
- [✓] Wi-Fi interface identified
- [✓] Current IPv4 address recorded
- [✓] DHCP reservation configured
- [✓] Reserved address verified


## 4. AdGuard Home Installation

### Objective

Install AdGuard Home natively on Raspberry Pi OS Lite 64-bit, without Docker.

### 4.1 Download the official installation script

Download the installer from the official AdGuard Home repository:

```bash
cd /tmp

curl -fsSL \
  https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh \
  -o AdGuardHome-install.sh
```

### 4.2 Review the installation script

Review the downloaded script before executing it:

```bash
less /tmp/AdGuardHome-install.sh
```

Press `q` to exit the viewer.

### 4.3 Install AdGuard Home

Execute the installation script:

```bash
sudo sh /tmp/AdGuardHome-install.sh
```

Follow the installation output and check for any errors.

### 4.4 Verify the service

Check the service status:

```bash
sudo systemctl status AdGuardHome --no-pager
```

Check whether the service is enabled at startup:

```bash
sudo systemctl is-enabled AdGuardHome
```

### 4.5 Verify the installed version

Try:

```bash
AdGuardHome --version
```

If the command is not found, use the typical installation path:

```bash
sudo /opt/AdGuardHome/AdGuardHome --version
```

### Verification

- [✓] Official installer downloaded
- [✓] Installer inspected
- [✓] Installation completed
- [✓] AdGuard Home service is active
- [✓] Service is enabled at startup
- [✓] Installed version recorded

**Important:** Do not change the router's DNS settings yet. First, verify the installation and complete the initial web setup.



