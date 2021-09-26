# Waydroid command line options

Waydroid offers a number of command line arguments and options in order to work with the various parts of the program.

### Usage

`waydroid [-h] [-V] [-l LOG] [--details-to-stdout] [-v] [-q]` 

### optional arguments

* -h, --help - show this help message and exit 
* -V, --version - show program's version number and exit 
* -l LOG, --log LOG path - to log file \(default: /var/lib/waydroid\)
* --details-to-stdout - print details \(e.g. build output\) to stdout, instead of writing to the log 
* -v, --verbose - write even more to the logfiles \(this may reduce performance\) 
* -q, --quiet - do not output any log messages
* -f - Force options \(used with 'init' commands\)
* -i LOCATION, Init from specified location \(default: /usr/share/waydroid-extra/images\) _\*used with init action\*_

### Actions 

You can use the following actions with the waydroid tool

* status - quick check for the waydroid 
* log - follow the waydroid logfile 
* init - set up waydroid specific configs and install images 
* upgrade - upgrade images 
* session - session controller 
* container - container controller 
* app - applications controller \(see: [Install and Run Android Applications](install-and-run-android-applications.md)\)
* prop - android properties controller 
* show-full-ui - show android full screen in window 
* shell - run remote shell command 
* logcat - show android logcat

### Examples

* log:

  ```bash
  waydroid log > ~/waydroid-log.txt
  ```

* logcat:

  ```bash
  sudo waydroid logcat > ~/waydroid-logcat.tx
  ```

* Init for test builds:  
  Create the folder: `usr/share/waydroid-extra/images` and extract your customized images there.   
  First, you need to do a little cleanup \(if this fails, reboot and try again\):

  ```bash
  sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid
  ```

  Then run:

  ```bash
  sudo waydroid init -f
  sudo waydroid init
  ```

  Or, if you have your test images in another location \(ex: ~/Downloads/test\_build/\), then run:

  ```bash
  sudo waydroid init -f
  sudo waydroid init -i ~/Downloads/test_build
  ```



