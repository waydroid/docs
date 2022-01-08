# Waydroid Prop Options

Waydroid uses various properties in order to tell the underlying Android system how to behave in a few places. To do this, we use the `waydroid prop` command. To unset a prop, `waydroid prop set <property> ""`

### Properties

* **waydroid prop set persist.waydroid.multi\_windows** true/false \(bool\) Enables/Disables persistent freeform window mode 
* **waydroid prop set persist.waydroid.invert\_colors** true/false \(bool\) Swaps the color space from RGBA to BGRA \(only works with our patched mutter so far\) 
* **waydroid prop set persist.waydroid.height\_padding** 0-9999 \(int\) Adjust Height padding \(30 will allow you to use navbar on mobile\) 
* **waydroid prop set persist.waydroid.width\_padding** 0-9999 \(int\) Adjust width padding 
* **waydroid prop set waydroid.display\_width** 0-9999 \(int\) \(auto-generated\) Auto generated size of Waydroid screen 
* **waydroid prop set persist.waydroid.width** 0-9999 \(int\) Used for user to override desired resolution 
* **waydroid prop set persist.waydroid.suspend** true/false \(bool\) Keep Waydroid awake and do not let container sleep





