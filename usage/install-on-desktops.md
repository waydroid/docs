# Install Instructions

## Arch Linux&#x20;

Some of our friends have started putting together all the install instructions for Arch over on the arch wiki:

{% embed url="https://wiki.archlinux.org/title/Waydroid" %}

## Postmarket OS

Thanks to the Postmarket community, you can also find instructions and troubleshooting tips on their wiki:

{% embed url="https://wiki.postmarketos.org/wiki/Waydroid" %}

## Mobian

The community was kind enough to post the install instructions for Mobian on their Doku pages:

{% embed url="https://wiki.mobian-project.org/doku.php?id=waydroid" %}

## Zorin OS

User @Aman9das has put together a detailed guide for installing Waydroid on Zorin OS:

{% embed url="https://github.com/Aman9das/Waydroid_Setup_Guide" %}

## Sailfish OS

A few of the contributors to sailfishos-open have put together a resource for installing Waydroid on the OS:

{% embed url="https://github.com/sailfishos-open/waydroid" %}

## Fedora

User Aleasto has put together a nice guide for Fedora that does not require a 3rd party kernel install:

{% embed url="https://copr.fedorainfracloud.org/coprs/aleasto/waydroid" %}

Otherwise, Karuboniru's blog post details the steps needed to get Waydroid up and running with kernel modifications:

{% embed url="https://yanqiyu.info/2021/10/25/waydroid-fedora" %}

## KISS Linux

User Mederim has come up with a guide for getting Waydroid on KISS Linux:

{% embed url="https://github.com/Mederim/kiss-waydroid" %}



## Ubuntu/Debian Based Install Instructions

### Installation

These instructions work for ubuntu focal, ubuntu hirsute, debian bullseye, droidian, ubports, and likely more. We will continue to update this document as the project further develops

### Install Pre-requisites

```bash
sudo apt install curl -y
```

Waydroid requires the following in order to work properly on your PC:

* python3
* lxc
* curl
* Wayland session manager _**IMPORTANT!!**_

> _**NOTES**:_
>
> * ⚠️ NVIDIA GPUs do not work as of now, try using iGPU of your CPU or software rendering instead.
> * _**Wayland session manager**_ comes with distros running GNOME by default (Ubuntu, Pop!\_OS, Fedora, etc), so no need to install separately.
> * Other desktop environments/window managers, might not support Wayland out of the box. (KDE Plasma does after 5.21)

### Install Waydroid

Install ca-certificates, if not already installed.

```bash
sudo apt install ca-certificates
```

Check your distro (codename) for the next step

```bash
lsb_release -c
```

Add the repo to your `sources.list`

* **Add waydroid repo** _(for droidian & ubports, this step can be skipped)_ Replace `DISTRO="bullseye"` with your current target. Options: **focal**, **bullseye**, **hirsute**

```bash
export DISTRO="bullseye" && \
sudo curl -# --proto '=https' --tlsv1.2 -Sf https://repo.waydro.id/waydroid.gpg --output /usr/share/keyrings/waydroid.gpg && \
echo "deb [signed-by=/usr/share/keyrings/waydroid.gpg] https://repo.waydro.id/ $DISTRO main" > ~/waydroid.list && \
sudo mv ~/waydroid.list /etc/apt/sources.list.d/waydroid.list && \
sudo apt update
```

**install Waydroid:**

```bash
sudo apt install waydroid -y
```

**And start the init process:**

```bash
sudo waydroid init
```

**Then start the waydroid container service (or just simply reboot):**

```bash
sudo systemctl start waydroid-container
```

## Troubleshooting

### Manually Starting Waydroid

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

### Launch Waydroid In Full-Screen Mode:

_(This can be run while Waydroid is running, or used to start it in full-screen mode)_

```bash
waydroid show-full-ui
```

### Launch Waydroid In Multi-Window Mode:

First we need to set the property while a Waydroid session is running:

```bash
waydroid prop set persist.waydroid.multi_windows true
```

After that, we can restart the container:

```
sudo systemctl restart waydroid-container
```

Then we are ready to launch an app, and it will start in multi-window mode

## Reinstalling Waydroid

Sometimes things don't go as planned and you need to remove it all and start over. To do that, follow the steps below:

First, make sure you have stopped the session and containers:

```bash
waydroid session stop
sudo waydroid container stop
```

Then it is safe to remove Waydroid:

```bash
sudo apt remove waydroid
```

After you remove Waydroid, reboot.

Then once logged back in, we need to do a little cleanup:

```bash
sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid ~/.share/waydroid ~/.local/share/applications/*aydroid* ~/.local/share/waydroid
```

Then can reinstall and run the init command again:

```bash
sudo apt install waydroid
sudo waydroid init
```
