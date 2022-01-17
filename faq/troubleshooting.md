---
description: If you run into issues, take a look at the official Issue Tracker: [Waydroid issue tracker](https://github.com/waydroid/waydroid/issues)
---

#### General tips
Waydroid is in rapid developement so if you face issues, here is a good list of steps to do first:

1. Make sure your Waydroid package is up to date;
2. Make sure you have the latest Waydroid image by running # waydroid upgrade;
3. Reset Waydroid: 
    * stop the `waydroid-container.service` `# systemctl stop waydroid-container.service`
    * cleanup `sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid ~/.share/waydroid ~/.local/share/applications/*aydroid* ~/.local/share/waydroid`
    * initialise `# waydroid init -f` or `# waydroid init -f -i /usr/share/waydroid-extra/images`
    * start the service again `# systemctl start waydroid-container.service`

#### Failed to start Clipboard manager service

Install [pyclip](https://repology.org/project/python:pyclip/versions)

#### Sometimes the physical keyboard does not work

Press Left Alt key.

#### Commands inside Waydroid shell outputs inaccessible or not found

On Arch based distributions there's a "bug" that may appear while working with lxc-attach that may cause this issue with commands inside waydroid shell like adbd or settings. A possible workaround for this would be replace the `# waydroid shell` command with `# lxc-attach -P /var/lib/waydroid/lxc/ -n waydroid --clear-env`.

#### WARNING: Service manager /dev/binder has died

See https://github.com/waydroid/waydroid/issues/136
You should enable [PSI](https://www.kernel.org/doc/html/latest/accounting/psi.html). Add `psi=1` to kernel command line.

#### Failed to load bpf program: (null)

Add `/etc/systctl.conf` file, `unprivileged_bpf_disabled=0`. Then reboot
