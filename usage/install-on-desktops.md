# Desktop Install Instructions

## Ubuntu/Debian Based Installation

\(for ubuntu focal and debian bullseye\)

### Prerequisites

Waydroid requires the following in order to work properly on your PC:

* python3
* lxc

### Install

Add the repo to your sources.list 

* **Option 1:  Using mrcyjanek-repo**  
  \(focal\):

  ```bash
  wget 'https://static.mrcyjanek.net/abstruse/apt-repository/mrcyjanek-repo/mrcyjanek-repo_2.0-1_all.deb' -O cyjanrepo.deb && sudo apt install ./cyjanrepo.deb && rm ./cyjanrepo.deb && rm -rf /etc/apt/sources.list.d/cyjan.list && echo 'deb [signedby=/usr/share/keyrings/mrcyjanek-archive-keyring.gpg] https://static.mrcyjanek.net/abstruse/apt-repository/ focal main' > /etc/apt/sources.list.d/cyjan.list && sudo apt update
  ```

  \(bullseye\):

  ```bash
  wget 'https://static.mrcyjanek.net/abstruse/apt-repository/mrcyjanek-repo/mrcyjanek-repo_2.0-1_all.deb' -O cyjanrepo.deb && sudo apt install ./cyjanrepo.deb && rm ./cyjanrepo.deb && rm -rf /etc/apt/sources.list.d/cyjan.list && echo 'deb [signedby=/usr/share/keyrings/mrcyjanek-archive-keyring.gpg] https://static.mrcyjanek.net/abstruse/apt-repository/ bullseye main' > /etc/apt/sources.list.d/cyjan.list && sudo apt update
  ```

* **Option 2: Ubuntu-Web repo**  
  \(ubuntu-web mirror\):

  ```bash
  wget https://waydroid.ubuntu-web.org/waydroid.key && sudo apt-key add waydroid.key && rm -f waydroid.key && echo 'deb https://waydroid.ubuntu-web.org/waydroid unstable main' | sudo tee /etc/apt/sources.list.d/waydroid.list && sudo apt-get update
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

