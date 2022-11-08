# Waydroid Prop Options

Waydroid uses various properties in order to tell the underlying Android system how to behave in a few places.
To do this, we use the `waydroid prop set <property> <value>` command.
To unset a prop, `waydroid prop set <property> ""`

### Properties

* **waydroid prop set persist.waydroid.multi\_windows** true/false \(bool\) Enables/Disables persistent freeform window mode 
* **waydroid prop set persist.waydroid.cursor_on_subsurface** true/false \(bool\) Workaround for showing the cursor in multi_windows mode on some compositors
* **waydroid prop set persist.waydroid.invert\_colors** true/false \(bool\) Swaps the color space from RGBA to BGRA \(only works with our patched mutter so far\) 
* **waydroid prop set persist.waydroid.height\_padding** 0-9999 \(int\) Adjust Height padding \(30 will allow you to use navbar on mobile\) 
* **waydroid prop set persist.waydroid.width\_padding** 0-9999 \(int\) Adjust width padding 
* **waydroid prop set waydroid.display\_width** 0-9999 \(int\) \(auto-generated\) Auto generated size of Waydroid screen 
* **waydroid prop set persist.waydroid.width** 0-9999 \(int\) Used for user to override desired resolution 
* **waydroid prop set persist.waydroid.suspend** true/false \(bool, default: false\) Let the Waydroid container sleep (after the display timeout) when no apps are active

#### Modify app behaviour
* **waydroid prop set persist.waydroid.fake_touch** (string) Comma ',' separated list of package names for which mouse inputs should be interpreted as touch inputs instead. Supports wildcards with `*`. For example, set this to `"com.rovio.*"` to match all games by Rovio
* **waydroid prop set persist.waydroid.fake_wifi** (string) Comma ',' separated list of package names for which the system will always appear as if connected to wifi. Supports wildcards with `*`. For example, set this to `"com.gameloft.*"` to match all games by Gameloft
