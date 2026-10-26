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
* **IPTABLES**
Check if your IPTABLES it's set the FORWARD policy with DROP
```bash
iptables --list-rules | grep FORWARD 
```
If yes, set ACCEPT
```bash
iptables -P FORWARD ACCEPT
```

### Docker sets the FORWARD policy to DROP

With its iptables firewall backend, Docker can set the `FORWARD` policy to
`DROP` when it enables IP forwarding. This can block Waydroid internet
traffic. See
[waydroid#509](https://github.com/waydroid/waydroid/issues/509) and
[waydroid#2023](https://github.com/waydroid/waydroid/issues/2023).

Instead of `iptables -P FORWARD ACCEPT`, which opens forwarding for every
interface, allow only the Waydroid bridge. These instructions apply to
Docker's [iptables firewall backend](https://docs.docker.com/engine/network/firewall-iptables/),
including the `iptables-nft` compatibility frontend. Docker's native
[nftables backend](https://docs.docker.com/engine/network/firewall-nftables/)
does not create a `DOCKER-USER` chain and needs different rules.
Use the same iptables frontend as Docker for the commands below:

```bash
sudo iptables -I DOCKER-USER -i waydroid0 -j ACCEPT
sudo iptables -I DOCKER-USER -o waydroid0 -j ACCEPT
sudo iptables -I FORWARD -i waydroid0 -j ACCEPT
sudo iptables -I FORWARD -o waydroid0 -j ACCEPT
```

If Android can reach the gateway (`192.168.240.1`) but not the internet,
also add NAT for the Waydroid subnet. Change `192.168.240.0/24` if you set a
different `LXC_NETWORK` in `waydroid-net.sh`:

```bash
sudo iptables -t nat -A POSTROUTING -s 192.168.240.0/24 ! -d 192.168.240.0/24 -j MASQUERADE
```

If Android gets no IPv4 address at all, check the host `INPUT` chain too.
When `iptables-nft` prints `iptables-legacy tables present`, Waydroid's DHCP
and DNS rules can be in the legacy tables while UFW or another firewall drops
the same packets in nftables. An `ACCEPT` in one backend does not override a
`DROP` in the other. With UFW, allow DHCP and DNS on the Waydroid bridge:

```bash
sudo ufw allow in on waydroid0 to any port 67 proto udp
sudo ufw allow in on waydroid0 to any port 53
```

These rules are lost on reboot. To apply them at each boot, after Docker and
Waydroid, save this script as `/usr/local/sbin/waydroid-nat.sh` and make it
executable (`sudo chmod +x /usr/local/sbin/waydroid-nat.sh`). It adds each
rule only if it is missing, so you can run it more than once. The script
defaults to `iptables-nft`; set `IPT` to the executable used by Docker on
your host if it uses a different frontend:

```sh
#!/bin/sh
# Allow and NAT Waydroid traffic when Docker sets the FORWARD policy to DROP.
IPT=/usr/sbin/iptables-nft
[ -x "$IPT" ] || IPT=/usr/sbin/iptables
SUBNET=192.168.240.0/24

$IPT -C FORWARD -i waydroid0 -j ACCEPT 2>/dev/null || $IPT -I FORWARD -i waydroid0 -j ACCEPT
$IPT -C FORWARD -o waydroid0 -j ACCEPT 2>/dev/null || $IPT -I FORWARD -o waydroid0 -j ACCEPT
if $IPT -L DOCKER-USER -n >/dev/null 2>&1; then
  $IPT -C DOCKER-USER -i waydroid0 -j ACCEPT 2>/dev/null || $IPT -I DOCKER-USER -i waydroid0 -j ACCEPT
  $IPT -C DOCKER-USER -o waydroid0 -j ACCEPT 2>/dev/null || $IPT -I DOCKER-USER -o waydroid0 -j ACCEPT
fi
$IPT -t nat -C POSTROUTING -s $SUBNET ! -d $SUBNET -j MASQUERADE 2>/dev/null || \
  $IPT -t nat -A POSTROUTING -s $SUBNET ! -d $SUBNET -j MASQUERADE
```

Then create `/etc/systemd/system/waydroid-nat.service`:

```ini
[Unit]
Description=Allow Waydroid traffic through the Docker firewall policy
After=docker.service waydroid-container.service network-online.target
Wants=waydroid-container.service

[Service]
Type=oneshot
ExecStart=/usr/local/sbin/waydroid-nat.sh
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

Enable it:

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now waydroid-nat.service
```

If you restart Docker, run `sudo systemctl restart waydroid-nat.service`
again.
