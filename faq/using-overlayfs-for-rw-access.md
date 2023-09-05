# Using OverlayFS for R/W Access

If your current distro supports overlayfs, then you should just be able to use our default overlay by using the following command:

  ```
  mount -o rw,remount /var/lib/waydroid/rootfs
  ```
