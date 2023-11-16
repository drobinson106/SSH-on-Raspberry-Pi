# SSH-on-Raspberry-Pi
## Enable SSH on Raspbery Pi
### Update Package List
Update your package list to ensure you have the latest versions of the software
```bash
sudo apt update
```

### Install SSH Server
Make sure you have the SSH server installed on teh Raspberry Pi OS
```bash
sudo apt install openssh-server
```

### Start SSH Service:
Enable the SSH service so it starts on boot
```bash
sudo systemctl enable ssh
```
Start the SSH service
```bash
sudo systemctl start ssh
```
To esure that SSH was succeffully started check the status
```bash
sudo systemctl status ssh
```
