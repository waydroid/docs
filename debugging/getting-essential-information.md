# Getting Essential Information

Useful information belongs in two places the methods of getting this information are as follows. If someone asks for the logs, it is best to give them the full output of these commands as well as include them on any issue tickets you create:

`sudo systemctl status waydroid-container.service`

`waydroid log`

`sudo waydroid logcat > ~/waydroid-logcat.txt`

It is also important to make sure your kernel supports binder and either ashmem or memfd, you can verify support in your kernel by using this command. 

`zgrep -i -e android -e memfd -e ashmem /proc/config.gz`

Or on Debian based distros:

`grep -i -e android -e memfd -e ashmem "/boot/config-$(uname -r)"`

If you do not have support, you may need to change to a supported kernel or look at patched anbox-modules.dkms.

Another important piece of information is knowing what linux enviroment you are using. These two commands contain the relevant information:

`lsb_release -a` and `uname -a`

