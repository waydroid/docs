# Setting up a shared folder

User @wachidadinugroho has worked out the details on how to setup a shared folder to be used between Waydroid and your host filesystem.&#x20;

Setting up a shared folder will allow the user to copy/paste files from the host and they appear inside waydroid/android.\
\
&#x20;`sudo mount --bind <source> ~/.local/share/waydroid/data/media/0/<target>`

Then verify that the target folder exists:&#x20;

&#x20;`sudo ls ~/.local/share/waydroid/data/media/0/`\
\
**Examples:**

```
 sudo mount --bind ~/Documents ~/.local/share/waydroid/data/media/0/Documents 
 sudo mount --bind ~/Downloads ~/.local/share/waydroid/data/media/0/Download 
 sudo mount --bind ~/Music ~/.local/share/waydroid/data/media/0/Music 
 sudo mount --bind ~/Pictures ~/.local/share/waydroid/data/media/0/Pictures 
 sudo mount --bind ~/Videos ~/.local/share/waydroid/data/media/0/Movies
```

You can also make your own custom mount point to cater to your needs.
