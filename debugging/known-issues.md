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

### Container fails to start after upgrade to Android 13 (LineageOS 20)

From Android 13 onwards, the filesystem on your home directory needs to support ACLs. If you use BTRFS, for instance with an encrypted `systemd-homed` directory, check that it isn't mounted with the `noacl` mount option.

If you are using `systemd-homed`, create the file `/etc/systemd/system/systemd-homed.service.d/btrfs-acl.conf` containing the following.

```
[Service]
Environment=SYSTEMD_HOME_MOUNT_OPTIONS_BTRFS=acl,compress=zstd:1,user_subvol_rm_allowed
```
