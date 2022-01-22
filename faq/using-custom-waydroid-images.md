# Using custom Waydroid images

In order to get custom images to work on Waydroid, there are just a couple extra steps needed.&#x20;

First, download the images manually from sourceforge, or use your custom built system.img and vendor.img produced from following the [Compile Instructions](../development/compile-waydroid-lineage-os-based-images.md#how-to-build). Then copy/move them to the following folder:

```
/usr/share/waydroid-extra/images/
```

&#x20;Then we need to re-init Waydroid in order for it to use the custom images:

```
waydroid init -f
```
