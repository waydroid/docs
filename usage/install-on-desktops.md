# Install Instructions

## Arch Linux&#x20;

Some of our friends have started putting together all the install instructions for Arch over on the arch wiki:

{% embed url="https://wiki.archlinux.org/title/Waydroid" %}

## Postmarket OS

Thanks to the Postmarket community, you can also find instructions and troubleshooting tips on their wiki:

{% embed url="https://wiki.postmarketos.org/wiki/Waydroid" %}

## Zorin OS

User @Aman9das has put together a detailed guide for installing Waydroid on Zorin OS:

{% embed url="https://github.com/Aman9das/Waydroid_Setup_Guide" %}

## Sailfish OS

A few of the contributors to sailfishos-open have put together a resource for installing Waydroid on the OS:

{% embed url="https://github.com/sailfishos-open/waydroid" %}

## Fedora

Waydroid can be installed from the official package repository.

```bash
sudo dnf install waydroid
```

After installing, launch Waydroid from the applications menu and proceed with the initialization by pasting these URLs in the OTA fields:

System OTA: `https://ota.waydro.id/system`

Vendor OTA: `https://ota.waydro.id/vendor`

### Silverblue/Kinoite/...

The same instructions apply to the Fedora Immutable variants, but you should use `rpm-ostree` instead of `dnf`

```bash
rpm-ostree install waydroid
```
## openSUSE Tumbleweed/Slowroll

User @runa-chin had created a detailed guide about installing Waydroid on openSUSE Tumbleweed or openSUSE Slowroll:

{% embed url="https://github.com/waydroid/waydroid/discussions/1463" %}

## KISS Linux

User Mederim has come up with a guide for getting Waydroid on KISS Linux:

{% embed url="https://github.com/Mederim/kiss-waydroid" %}

## Void Linux

Waydroid can be installed from the official package repository; also check `/usr/share/doc/waydroid/README.voidlinux` after installation for further instructions!

```bash
sudo xbps-install -S waydroid
```

## Ubuntu/Debian and derivatives

For Droidian and Ubuntu Touch, skip directly to the last step

Make sure you have Wayland Session enabled (Ubuntu 22.04+)

{% embed url="https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-22-04-desktop" %}

* Install pre-requisites
```bash
sudo apt install curl ca-certificates -y
```

* Add the official repository
```bash
curl -s https://repo.waydro.id | sudo bash
```
If the script fails to detect your distribution, you can provide a valid option by appending `-s <DISTRO>`.
Currently supported values are: **mantic**, **focal**, **jammy**, **kinetic**, **lunar**, **noble**, **plucky**, **questing**, **bookworm**, **bullseye**, **trixie**, **sid**

* Install waydroid
```bash
sudo apt install waydroid -y
```

Then start Waydroid from the applications menu.

## NixOS

NixOS community has a wiki page for WayDroid:

{% embed url="https://wiki.nixos.org/wiki/Waydroid" %}

# Troubleshooting

## Manually Starting Waydroid

To start Waydroid without systemctl, you need to follow a few simple steps

**Start the container first:**

```bash
sudo waydroid container start
```

**And in a new terminal tab, start the waydroid session (without** _**sudo**_**):**

```bash
waydroid session start
```

After that starts and you see "Android with user 0 is ready", it is safe to launch an app from the applications menu, or

## Launch Waydroid In Full-Screen Mode:

_(This can be run while Waydroid is running, or used to start it in full-screen mode)_

```bash
waydroid show-full-ui
```

## Launch Waydroid In Multi-Window Mode:

First we need to set the property while a Waydroid session is running:

```bash
waydroid prop set persist.waydroid.multi_windows true
```

After that, we can restart the session:

```
waydroid session stop
```

Then we are ready to launch an app, and it will start in multi-window mode

## Reinstalling Waydroid

Sometimes things don't go as planned and you need to remove it all and start over. To do that, follow the steps below:

First, make sure you have stopped the session and containers:

```bash
waydroid session stop
sudo waydroid container stop
```

Then it is safe to remove Waydroid. For example, on debian or ubuntu:

```bash
sudo apt remove waydroid
```

After you removed Waydroid, reboot.

Then once logged back in, we need to do a little cleanup:

```bash
sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid ~/.share/waydroid ~/.local/share/applications/*aydroid* ~/.local/share/waydroid
```

Then you can follow the install instructions again.
