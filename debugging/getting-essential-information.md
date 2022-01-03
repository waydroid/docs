# Getting Essential Information

Useful information belongs in two places the methods of getting this information are as follows. if someone asks for the logs, it is best to give them the full output of these commands as well as include them on any issue tickets you create.

`sudo systemctl status waydroid-container.service`

`waydroid log`

`sudo waydroid logcat > ~/waydroid-logcat.txt`

It is also important to make sure your kernel supports ashmem and binder, you can verify support in your kernel by using this command. if you do not have support, you may need to change to a supported kernel or look at patched anbox-modules.dkms

`zgrep -i -e android -e ashmem /proc/config.gz`&#x20;

Another important piece of information is knowing what linux enviroment you are using. these two commands contain the relevant information

`lsb_release -a` and `uname -a`

