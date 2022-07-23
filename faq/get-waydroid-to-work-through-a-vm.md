---
description: This also applies to any unsupported GPU's as well (like nVidia)
---

# Get Waydroid to work through a VM

In order to get Waydroid to work through a VM, you may need to adjust a couple things in waydroid\_base.prop.

```
nano /var/lib/waydroid/waydroid_base.prop
```

Change both these to what is shown below:

```
ro.hardware.gralloc=default
ro.hardware.egl=swiftshader
```

Restart the container afterwards:

```js
sudo systemctl restart waydroid-container
```

### Qemu
Qemu is the only VM known to have working 3d acceleration (possibly crosvm too).

Qemu needs to have virtio-gpu setup with 3d graphics acceleration enabled for both virtio-gpu and the display (Ie. Spice, SDL etc.). Using EGL-headless (useful for dedicated VM servers) will also work with waydroid these will work on any qemu which has 3d acceleration built for it.

Another method to use gpu passthrough on the VM, this will work on any virtual machine software that supports it.
