### SSH on Raspberry Pi

#### Table of Contents
- [Update Package List](#update-package-list)
- [Install SSH Server](#install-ssh-server)
- [Start SSH Service](#start-ssh-service)
- [Find Public IP](#find-public-ip)
- [Enable Port Forwarding](#enable-port-forwarding)
  - [Find Gateway Router IP](#find-gateway-router-ip)
  - [Navigate to the Gateway router portal](#navigate-to-the-gateway-router-portal)
  - [Navigate to the NAT settings in router portal](#navigate-to-the-nat-settings-in-router-portal)
  - [Setting up Port Forwarding for SSH](#setting-up-port-forwarding-for-ssh)
- [Connecting through SSH](#connecting-through-ssh)

#### Update Package List

Ensure you have the latest versions of the software:

```
sudo apt update
```

#### Install SSH Server

Install the SSH server on the Raspberry Pi OS:

```
sudo apt install openssh-server
```

#### Start SSH Service

Enable the SSH service to start on boot:

```
sudo systemctl enable ssh
sudo systemctl start ssh
sudo systemctl status ssh
```

#### Find Public IP

Find the public IPv4 address of your current network:

```
curl -4 ifconfig.me
```

#### Enable Port Forwarding

Home networks typically employ a gateway router that directs incoming internet connections to the appropriate device within the local network. To reach a specific device from the internet, port forwarding must be enabled on the router. This setup allows the router to relay external requests to the targeted device's IP and port.

##### Find Gateway Router IP

To find the Gateway Router's IP address:

```
ip route | grep default
```

##### Navigate to the Gateway router portal

Input the gateway router's IP address into your web browser.

##### Navigate to the NAT settings in router portal

To get NAT settings:

From the portal homepage, navigate to **Firewall** > **NAT/Gaming**. These settings are protected, so you will need to retrieve your router's access code from the side of your router and input them to access these settings. (Note: I have ATT, so this may be different for you.)

##### Setting up Port Forwarding for SSH

Here we will finally create a custom service. For my service, I included these parameters:

- **Name:** My Raspberry Pi
- **Global Port Range:** 2222
  - This is the port that will be accessed on your gateway router (Port 2222 chosen for obscurity, but SSH Key Authentication is still recommended).
- **Base Host Port:** 22
  - This is the port that the connection will be connected to on the Raspberry Pi (Port 22 is the usual port for SSH).
- **Protocol:** TCP/UDP

#### Connecting through SSH

While your Raspberry Pi is open, on another device input this:

```
ssh -p 2222 user@pi-public-ip
```

- `pi` = username of the user logged in on the Raspberry Pi.
- `pi-public-ip` = Public IP of the network that the Raspberry Pi is connected to.

Finally, you will be prompted for the password of the user you are trying to SSH in, and then you're in!
