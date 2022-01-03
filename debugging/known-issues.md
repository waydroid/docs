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

Dual GPUs are known to cause an issue where the display is garbled or flickering. there are two fixes for this.&#x20;

the first method is to use `gralloc.gbm.device=/dev/dri/renderD128` replacing `D128` with whichever gpu you use.

Failing this, there is a script located [`here`](https://github.com/Quackdoc/waydroid-scripts/blob/main/waydroid-choose-gpu.sh). this script will modify the LXC binding so only one GPU gets used by waydroid
