# Waydroid Prop Options

Waydroid uses various properties in order to tell the underlying Android system how to behave in a few places.
To do this, we use the `waydroid prop set <property> <value>` command.
To unset a prop, `waydroid prop set <property> ""`.
Most settings require restarting the waydroid session to apply.

### Waydroid behaviour

* **waydroid prop set persist.waydroid.multi\_windows** true/false \(bool\) Enables/Disables window integration with the desktop
* **waydroid prop set persist.waydroid.height\_padding** 0-9999 \(int\) Adjust height padding
* **waydroid prop set persist.waydroid.width\_padding** 0-9999 \(int\) Adjust width padding
* **waydroid prop set persist.waydroid.width** 0-9999 \(int\) Used for user to override desired resolution
* **waydroid prop set persist.waydroid.height** 0-9999 \(int\) Used for user to override desired resolution
* **waydroid prop set persist.waydroid.suspend** true/false \(bool, default: true on kernel 4.9 and later\) Let the Waydroid container sleep (after the display timeout) when no apps are active
* **waydroid prop set persist.waydroid.uevent** true/false \(bool, default: false) Allow android direct access to hotplugged devices
* **waydroid prop set persist.waydroid.reverse_scrolling** true/false (\bool default: false) Invert the direction of scrolling

#### App behaviour
* **waydroid prop set persist.waydroid.fake_touch** (string, 91 character limit) Comma separated list of package names for which mouse inputs should be interpreted as touch inputs instead. Supports wildcards with `*`. For example, set this to `"com.rovio.*"` to match all games by Rovio.
* **waydroid prop set persist.waydroid.fake_wifi** (string, 91 character limit) Comma separated list of package names for which the system will always appear as if connected to wifi. Supports wildcards with `*`. For example, set this to `"com.gameloft.*"` to match all games by Gameloft.

### Debug
* **waydroid prop set persist.waydroid.no_presentation** true/false \(bool\) Disables the wp_presentation protocol
* **waydroid prop set persist.waydroid.invert\_colors** true/false \(bool\) Swaps the color space from RGBA to BGRA
* **waydroid prop set persist.waydroid.cursor_on_subsurface** true/false \(bool\) Draw the cursor on a subsurface, rather than on the cursor surface
* **waydroid prop set persist.waydroid.cursor_force_shm** true/false \(bool\) Always submit wl_shm buffers for the cursor surface
* **waydroid prop set persist.waydroid.no_background_subsurface** true/false \(bool\) Do not submit a black background subsurface
* **waydroid prop set persist.waydroid.use_subsurface** true/false (\bool\) Submit overlayed subsurfaces rather than letting Android compose the stack
