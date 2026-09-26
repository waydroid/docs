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

First, find the host interface that provides internet access. Its name appears
after `dev` in the output below (for example, `wlan0` or `eth0`).

```bash
ip route get 1.1.1.1
```

Replace `HOST_INTERFACE` with that interface name, then allow Waydroid's
forwarded traffic, DHCP, and DNS:

```bash
sudo ufw route allow in on waydroid0 out on HOST_INTERFACE from 192.168.240.0/24
sudo ufw allow in on waydroid0 proto udp to any port 67
sudo ufw allow in on waydroid0 proto udp from 192.168.240.0/24 to 192.168.240.1 port 53
sudo ufw allow in on waydroid0 proto tcp from 192.168.240.0/24 to 192.168.240.1 port 53
```

If the host switches between multiple internet interfaces, add the first rule
for each interface that Waydroid should use. These rules keep UFW's default
forwarding policy unchanged and restrict DHCP and DNS access to `waydroid0`.

* **IPTABLES**
Check if your IPTABLES it's set the FORWARD policy with DROP
```bash
iptables --list-rules | grep FORWARD 
```
If yes, set ACCEPT
```bash
iptables -P FORWARD ACCEPT
```
