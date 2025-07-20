# Google Play Protect certification

When launching waydroid with GAPPS for the first time you will be notified that the device is not certified for **Google Play Protect**.
You can follow the instructions on screen to self certify your device, or here's a shortcut:

* Open a Terminal
* Run the following command:
```
sudo waydroid shell -- sh -c "sqlite3 /data/data/*/*/gservices.db 'select * from main where name = \"android_id\";'"
```
* Use the string of numbers printed by the command to register the device on your Google Account at [https://www.google.com/android/uncertified](https://www.google.com/android/uncertified)
* Give the Google services some minutes to reflect the change, then restart waydroid with:
```
waydroid session stop
```
