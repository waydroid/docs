---
description: Correct the colors when using a Mutter shell
---


#Color Correction In Mutter

###Using Patched Mutter

If you're using the patched Mutter version from the Waydroid repo with the color inversion patch (or Gnome 42 or higher), or mutter-rounded, then Waydroid should display properly.

###Using Standard Mutter

If you aren't able to install the patched version of Mutter, you can run this in the host shell:

```bash
waydroid prop set persist.waydroid.invert_colors true
```

Note that with this option enabled, you should not use this in combination with multi-window mode.

If you want to do it from inside the Android shell:

```bash
settings put secure accessibility_display_inversion_enabled 1
```

Running this inside the Android shell will correct all of the colors except for the boot animation.

