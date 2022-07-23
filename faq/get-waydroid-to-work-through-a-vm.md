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

Reload the waydroid configuration with:

```js
sudo waydroid upgrade -o
```
