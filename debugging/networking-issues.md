# Networking Issues

### Getting network info

Run the command below to get the information of various network interfaces.

`ip addr show`

### Setting up your firewall

* **firewalld**
```bash
firewall-cmd --zone=trusted --add-interface=waydroid0
```

* **UFW** or **GUFW**
```bash
sudo ufw allow 53
sudo ufw allow 67
sudo ufw default allow FORWARD
```

### Disable nftables and iptables-legacy

if it still does now work, you can follow the [reply to this issue](https://github.com/waydroid/waydroid/issues/143#issuecomment-1520857943) and run:

```
sudo sed -i~ -E 's/=.\$\(command -v (nft|ip6?tables-legacy).*/=/g' \
     /usr/lib/waydroid/data/scripts/waydroid-net.sh
```

This command disables `nft` and `iptables-legacy`.
