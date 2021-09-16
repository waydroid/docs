# Desktop Install Instructions

## Ubuntu/Debian Based Installation

\(for ubuntu focal & hirsute along with debian bullseye\)

### Prerequisites

Waydroid requires the following in order to work properly on your PC:

* python3
* lxc
* curl

### Install

Add the repo to your sources.list

* **Unified Install**  
  Replace `DISTRO="bullseye"` with your current target.  
  Options: **focal**, **bullseye**, **hirsute**

  ```bash
  export DISTRO="bullseye" && \
  curl https://repo.waydro.id/waydroid.gpg > /usr/share/keyrings/waydroid.gpg && \ 
  echo "deb [signed-by=/usr/share/keyrings/waydroid.gpg] https://repo.waydro.id/ $DISTRO main" > /etc/apt/sources.list.d/waydroid.list && \
  sudo apt update
  ```

Then install Waydroid:

```bash
apt install waydroid
```

And start the init process:

```bash
sudo waydroid init
```

Then start the waydroid-container service:

```bash
sudo systemctl start waydroid-container
```

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
sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid
```

Then can reinstall and run the init command again:

```bash
sudo apt install waydroid
sudo waydroid init
```

