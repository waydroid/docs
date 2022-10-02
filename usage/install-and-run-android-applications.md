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

To launch an app using CLI, you would want to use the `waydroid app launch <appname>` command:

```bash
waydroid app launch xyz.apk
```

You can also install Android applications from the command line.

```bash
waydroid app install xyz.apk
```

The apk files you will sometimes find on the internet tend to only have arm support, and will therefore not work on x86\_64.

You may want to install [F-Droid](https://f-droid.org) to get applications graphically. Note that the Google Play Store will not work as is, because it relies on the proprietary Google Play Services, which are not installed.
