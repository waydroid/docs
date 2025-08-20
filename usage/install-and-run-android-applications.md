# Install and Run Android Applications

Once installed you can launch Android application through your desktop Application Menu.
For example try to find a Contacts app.

Waydroid is able to perform a few various operations found by using the `waydroid app -h` command:

```bash
usage: waydroid app [-h] {install,remove,launch,list} ...

optional arguments:
  -h, --help            show this help message and exit

subaction:
  {install,remove,launch,list}
    install             push a single package to the container and install it
    remove              remove single app package from the container
    launch              start single application
    list                list installed applications
```

So to see a list of all available apps use:

```sh
waydroid app list
```

Now you see the Android package name of the app (it looks like `com.xxx.yyy`) and you can launch it from the commandline with `waydroid app launch`:

```sh
waydroid app launch com.android.contacts
```


You can install an Android application from `*.apk` package with `waydroid app install some_app.apk`.
The apk files you will sometimes find on the internet tend to only have ARM support, and will therefore not work on x86\_64.

As an example let's install the [F-Droid](https://f-droid.org) libre app store to get applications graphically:

```sh
wget -O /tmp/F-Droid.apk https://f-droid.org/F-Droid.apk
waydroid app install /tmp/F-Droid.apk
rm -f /tmp/F-Droid.apk
waydroid app launch org.fdroid.fdroid
```

With the F-Droid you may install more apps. You can also use the Play Store if you installed a [GAPPS image](../faq/using-custom-waydroid-images.md).


