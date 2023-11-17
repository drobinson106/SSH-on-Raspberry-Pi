# SSH-on-Raspberry-Pi
## Update Package List:
Update your package list to ensure you have the latest versions of the software
```bash
sudo apt update
```

## Install SSH Server:
Make sure you have the SSH server installed on teh Raspberry Pi OS
```bash
sudo apt install openssh-server
```

## Start SSH Service:
Enable the SSH service so it starts on boot
```bash
sudo systemctl enable ssh
```
Start the SSH service
```bash
sudo systemctl start ssh
```
To ensure that SSH was successfully started check the status
```bash
sudo systemctl status ssh
```

## FInd Public IP:
Find the public IPv4 address of your current network
```bash
curl -4 ifconfig.me
```

## Enable Port Forwarding:
Home networks typically employ a gateway router that directs incoming internet connections to the appropriate device within the local network. To reach a specific device from the internet, port forwarding must be enabled on the router. 
This setup allows the router to relay external requests to the targeted device's IP and port.

### Find Gateway Router IP
To find the Gateway Router's IP address 
```bash
ip route | grep default
```
### Navigate to the Gateway router portal 
Input the gateway router's IP address into your web browser

### Navigate to the NAT settings in router portal
To get NAT settings:
From the portal homepage **Firewall** > **NAT/Gaming**
These settings are protected so you will need to retrieve your router's access code from the side of your router and input them to access these settings
***Note I have ATT so this may be different for you**

### Setting up Port Forwarding for SSH
Here we will finally create a custom service, for my service I included these parameters:
Name: My Raspberry Pi
Global Port Range: 2222 
- This is the port that will be accessed on your gateway router (Port 2222 chosen for obscurity but SSH Key Authentication is still recommended)
Base Host Port: 22
- This is the port that the connection will be connected to on the Raspberry Pi (Port 22 is the usual port for SSH)
Protocol: TCP/UDP

