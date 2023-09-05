# Using custom Waydroid images

In order to get custom images to work on Waydroid, there are just a couple extra steps needed.

First, download the images (e.g. x86_64 gapps system and mainline vendor) manually [from sourceforge](https://sourceforge.net/projects/waydroid/files/images/) or use your custom built `system.img` and `vendor.img` produced from following the [Compile Instructions](../development/compile-waydroid-lineage-os-based-images.md#how-to-build).

Then copy/move them to the following folder:

```
/etc/waydroid-extra/images/
```

`/usr/share/waydroid-extra/images/` used to be the previously preferred path before `waydroid --version` 1.3.3 (it still is perfectly valid however right now as well).

An example of setting up from downloaded sourceforce zips (assuming terminal open in the directory where they were downloaded):

```sh
sudo mkdir -p /etc/waydroid-extra/images
sudo unzip lineage-*-system.zip -d /etc/waydroid-extra/images
sudo unzip lineage-*-vendor.zip -d /etc/waydroid-extra/images
rm lineage-*-system.zip lineage-*-vendor.zip
```

Then we need to re-init Waydroid in order for it to use the custom images:

```sh
sudo waydroid init -f
```
