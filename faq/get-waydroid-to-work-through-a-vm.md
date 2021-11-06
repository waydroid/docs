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
