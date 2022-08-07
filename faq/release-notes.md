# Release Notes

## Waydroid 1.2.1

### Improvements :-

  * Set sys.use_memfd=true if ashmem is not present
  * config: Switch to https for OTA channels
  * add size units and speed in download progress bar
  * Add an optional [properties] in waydroid.cfg
  * scripts: make sure misc subfolder exists
  * container: strip possible trailing newline from pid
  * lxc: Fix bad eol of proc dt values
  * Resume initialization if not complete
  * Remove downloaded system images which failed checksum verification
  * props: Use subprocess for host getprop

## Waydroid 1.2.0

### Improvements :-

  * config: Update waydroid ota channel urls
  * lxc: Get device info props from host
  * session: Nuke old data dir movement
  * lxc: Make sure vibrator sys nodes are writable
  * lxc: Add non-treble camera support
  * lxc: Skip host_perms on non treble devices
  * lxc: Add more sphal paths to find_hal
  * images: Decode http retrieve for older pythons
  * drivers: Add bonder nodes support
  * container: Add missing powervr nodes chmod
  * container: Use umount -l for schedtune
  * log: More resilient logging
  * net: Disable NFT by default
  * arch: detect armv8l as 32bit arm
  * drivers: Keep devices arg on modprobe
  * session: don't panic when removing old userdata if its not empty
  * lxc: do prepend colon to Android PATHs in shell
  * container: don't panic if binder device already exists
  * upgrade: log that no we will not upgrade if a preinstalled image exists

## Waydroid 1.1.1

### Improvements :-

  * lxc: Include tmp runtime dirs to container
  * session: Move waydroid user data to XDG_DATA_HOME
  * drivers: Allocate binder nodes dynamically
  * user_manager: Use one variable for apps dir
  * user: Create apps dir if doesn’t exists
  * lxc: workaround weird log permission bug

## Waydroid 1.1.0

### Improvements :-

  * tools: Fully restart services
  * container: Don’t burn XDG permissions
  * user: Only hide Waydroid app on multi-win
  * actions: Start session by lunching apps
  * data: Install Waydroid launcher by default
  * debian: Add systemd service
  * config: Store data in /var/lib/waydroid rather than /home/.waydroid
  * init: Add check for work dir before mkdir
  * data: Update app logo
  * Readme: Add documentation site
  * drivers: Improve binderfs loading
  * tools: Fix typo on stop container
  * tools: Drop requests library dependency
  * tools: Rename pre-init log file
  * tools: Remove unused requests import
  * ci: Add .abstruse.yml
  * tools: fix shell path env
  * user: Add “waydroid” prefix to desktop files
  * tools: Drop need of sudo as much as possible
  * lxc: Add WSLg support
  * lxc: Provide /var/run to container
  * lxc: Provide all fb and video nodes to container
  * container: Don’t crash on sensord
  * lxc: Mount /dev/null for container
  * lxc: Enable vndk lite for mainline devices
  * lxc: Use v4l2 camera hal on mainline
  * log: don't panic on ctrlc
  * debian: Add LXC as dependency
  * container: Umount on stop
  * upgrade: show progress

## Waydroid 1.0.0

  * Initial release
