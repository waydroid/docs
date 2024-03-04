# How to install an APK as system app via overlayfs without rooting or custom image

```
sudo install -vpD YourAPkName.apk /var/lib/waydroid/overlay/system/priv-app/YourAPkName/YourAPkName.apk
sudo systemctl restart waydroid-container
```
References: 
https://github.com/waydroid/waydroid/discussions/1001
https://github.com/waydroid/waydroid/issues/1109
