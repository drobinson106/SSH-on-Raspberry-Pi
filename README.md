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
To ensure that SSH was succeffully started check the status
```bash
sudo systemctl status ssh
```

## FInd Public IP:
Find the public IPv4 address of your current network
```bash
curl -4 ipconfig.me
```

## Enable Port Forwarding
Home networks typically employ a gateway router that directs incoming internet connections to the appropriate device within the local network. To reach a specific device from the internet, port forwarding must be enabled on the router. 
This setup allows the router to relay external requests to the targeted device's IP and port.

