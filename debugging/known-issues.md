# Known Issues

### Container fails to start: dnsmasq cannot open pid file

#### One cause for this issues is apparmor, the fix is as follows

Edit `/etc/apparmor.d/usr.sbin.dnsmasq` OR `/etc/apparmor.d/local/usr.sbin.dnsmasq`

adding the below to it.

```
@{run}/waydroid-lxc/ r,
@{run}/waydroid-lxc/* rw,
```

### Graphical issues.

Dual GPUs are known to cause an issue where the display is garbled or flickering.
You can try [this script](https://github.com/Quackdoc/waydroid-scripts/blob/main/waydroid-choose-gpu.sh) to choose which GPU should be used by Waydroid
