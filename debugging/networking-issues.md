# Networking Issues

### Getting network info

Run the command below to get the information of various network interfaces.

`ip addr show`

### Setting up your firewall

* **firewalld**
```bash
firewall-cmd --zone=trusted --add-interface=waydroid0 --permanent
```

* **UFW** or **GUFW**
```bash
sudo ufw allow 53
sudo ufw allow 67
sudo ufw default allow FORWARD
```
