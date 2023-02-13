---
description: This also applies to any unsupported GPU's as well (like nVidia)
---

# Get Waydroid to work through a VM

You can force Waydroid to run without GPU acceleration by modifying the waydroid configuration file:

```
nano /var/lib/waydroid/waydroid.cfg
```

Add the following lines in the `[properties]` section:

```
ro.hardware.gralloc=default
ro.hardware.egl=swiftshader
```

Apply the configuration with:

```js
sudo waydroid upgrade -o
```

### Qemu
Qemu is the only VM known to have working 3d acceleration (possibly crosvm too).

Qemu needs to have virtio-gpu setup with 3d graphics acceleration enabled for both virtio-gpu and the display (Ie. Spice, SDL etc.). Using EGL-headless (useful for dedicated VM servers) will also work with waydroid these will work on any qemu which has 3d acceleration built for it.

Another method to use gpu passthrough on the VM, this will work on any virtual machine software that supports it.
