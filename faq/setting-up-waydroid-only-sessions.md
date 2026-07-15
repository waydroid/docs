---
description: >-
  For some projects, you might want to have Linux only for backend or
  maintenance related tasks, while using the Waydroid full-screen UI as the main
  interface.
---

# Setting up Waydroid only Sessions

This document will review changes required for setting up wayland sessions for a full-screen Waydroid experience.

## Setting Up

In order to set this up, you will need to create a few files, depending on your default wayland session manager.&#x20;

Please create the files detailed by their contents using the contents below

### Cage

`/usr/share/wayland-sessions/waydroid.desktop` contents:

```
[Desktop Entry]
Name=WayDroid
Comment=Android OS in a container
Exec=/usr/bin/cage waydroid show-full-ui
Type=Application
```

### Mutter

`/usr/bin/mutter-session.sh` contents (make sure to mark the file as executable):

```
#!/bin/sh
mutter --wayland &
sleep 5
export DISPLAY=:1
waydroid show-full-ui
```

`/usr/share/wayland-sessions/mutter.desktop` contents:

```
[Desktop Entry]
Name=WayDroid on Mutter
Comment=Android OS in a container
Exec=/usr/bin/mutter-session.sh
Type=Application
```

### Weston

`~/.config/weston.ini` contents:

```
[libinput]
enable-tap=true

[shell]
panel-position=none
```

`/usr/bin/waydroid-session.sh` contents:

```
#!/bin/sh

# Launch waydroid from an X11 session, within a 9:16
# weston  window that vertically fills the screen

# REQUIRES-PACKAGE: x11-tools (xdpyinfo)
xdpyinfo \
| awk '/dimensions/{gsub("x"," ",$2);print $2"\n";quit}' \
| { read  xx yy
    weston --width=$((yy*9/16)) --height=${yy} & }

# WAYLAND_DISPLAY: Your personal value may end 
# with a different integer
export WAYLAND_DISPLAY=wayland-1
waydroid show-full-ui
```

`/usr/share/wayland-sessions/waydroid.desktop` contents:

```
[Desktop Entry]
Name=WayDroid on Weston
Comment=Android OS in a container
Exec=/usr/bin/waydroid-session.sh
Type=Application
```

### Wayfire

`/usr/bin/wayfire-session.sh` contents:

```
#!/bin/sh
wayfire &
export DISPLAY=:1
sleep 5
waydroid show-full-ui
```

`/usr/share/wayland-sessions/wayfire.desktop` contents:

```
[Desktop Entry] 
Name=waydroid on Wayfire 
Comment=Android OS in a container 
Exec=/usr/bin/wayfire-session.sh
Type=Application
```
