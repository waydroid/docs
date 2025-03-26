# Google Play Protect certification

When launching waydroid with GAPPS for the first time you will be notified that the device is not certified for **Google Play Protect**.
You can follow the instructions on screen to self certify your device, or here's a shortcut:

* Run `sudo waydroid shell`
* Inside the shell run this command:
```
ANDROID_RUNTIME_ROOT=/apex/com.android.runtime ANDROID_DATA=/data ANDROID_TZDATA_ROOT=/apex/com.android.tzdata ANDROID_I18N_ROOT=/apex/com.android.i18n sqlite3 /data/data/com.google.android.gsf/databases/gservices.db "select * from main where name = \"android_id\";"
```
* Use the string of numbers printed by the command to register the device on your Google Account at [https://www.google.com/android/uncertified](https://www.google.com/android/uncertified)
* Give the Google services some minutes to reflect the change, then restart waydroid
* You may also speed up this process by going to `Settings > Apps > Google Play Services`, select `Force Stop`, then `Storage > Clear Cache`, then open any of the GAPPS
