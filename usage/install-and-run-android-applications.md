# Install and Run Android Applications

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

You can install Android applications with:

```bash
waydroid app install xyz.apk
```

Then you can launch the application through your desktop Application Menu.

If you know the Android package name of the app (`com.xxx.yyy`) you can also use the commandline with:

```bash
waydroid app launch com.foo.bar
```

The apk files you will sometimes find on the internet tend to only have arm support, and will therefore not work on x86\_64.

You may want to install [F-Droid](https://f-droid.org) to get applications graphically. Or use the Play Store if you installed a GAPPS image.
