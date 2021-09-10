# Waydroid command line options

Waydroid offers a number of command line arguments and options in order to work with the various parts of the program.

### Usage

`waydroid [-h] [-V] [-l LOG] [--details-to-stdout] [-v] [-q]` 

### optional arguments

* -h, --help - show this help message and exit 
* -V, --version - show program's version number and exit 
* -l LOG, --log LOG path - to log file 
* --details-to-stdout - print details \(e.g. build output\) to stdout, instead of writing to the log 
* -v, --verbose - write even more to the logfiles \(this may reduce performance\) 
* -q, --quiet - do not output any log messages
* -f - Force options \(used with 'init' commands\)
* -i LOCATION, Init from specified location \(/usr/share/waydroid-extra/images\) _\*used with init action\*_    Example: `sudo waydroid init -i usr/share/waydroid-extra/images`

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

* log

  ```bash
  waydroid log > ~/waydroid-log.txt
  ```

* logcat

  ```bash
  sudo waydroid logcat > ~/waydroid-logcat.tx
  ```

