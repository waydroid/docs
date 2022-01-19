# Waydroid command line options

Waydroid offers a number of command line arguments and options in order to work with the various parts of the program.

## Usage

`waydroid [-h] [-V] [-l LOG] [--details-to-stdout] [-v] [-q]`

## optional arguments

* \-h, --help - show this help message and exit
* \-V, --version - show program's version number and exit
* \-l LOG, --log LOG path - to log file (default: /var/lib/waydroid)
* \--details-to-stdout - print details (e.g. build output) to stdout, instead of writing to the log
* \-v, --verbose - write even more to the logfiles (this may reduce performance)
* \-q, --quiet - do not output any log messages
* \-f - Force options (used with 'init' commands)
* \-i LOCATION, Init from specified location (default: /usr/share/waydroid-extra/images) _\*used with init action\*_

## Actions

You can use the following actions with the waydroid tool

* status - quick check for the waydroid
* log - follow the waydroid logfile
* init -option command - set up waydroid specific configs and install images
* upgrade - upgrade images
* session - session controller
* container - container controller
* app - applications controller (see: [Install and Run Android Applications](install-and-run-android-applications.md))
* prop - android properties controller
* show-full-ui - show android full screen in window
* shell - run remote shell command
* logcat - show android logcat

## Init Options

usage: waydroid init \[-h] \[-i IMAGES\_PATH] \[-f] \[-c SYSTEM\_CHANNEL] \[-v VENDOR\_CHANNEL] \[-r ROM\_TYPE] \[-s SYSTEM\_TYPE]

* \-h | --help : Show this help message and exit
* \-i IMAGES\_PATH | --images\_path IMAGES\_PATH : Custom path to waydroid images (default in /var/lib/waydroid/images)
* \-f | --force : Used when resetting or using custom images added to /usr/share/waydroid-extra/images
* \-c SYSTEM\_CHANNEL | --system\_channel SYSTEM\_CHANNEL : Custom system channel (options: OTA channel URL; default is Official OTA server)
* \-v VENDOR\_CHANNEL | --vendor\_channel VENDOR\_CHANNEL : Custom vendor channel (options: OTA channel URL; default is Official OTA server)
* \-r ROM\_TYPE | --rom\_type ROM\_TYPE : Rom type (options: "lineage", "bliss" or OTA channel URL; default is LineageOS)
* \-s SYSTEM\_TYPE | --system\_type SYSTEM\_TYPE : System type (options: VANILLA, FOSS or GAPPS; default is VANILLA)

## Log Options

usage: waydroid log \[-h] \[-n LINES] \[-c]

* \-h | --help : Show this help message and exit
* \-n LINES | --lines LINES : Count of initial output lines
* \-c | --clear : Clear the log

## Container Options

usage: waydroid container \[-h] {start,stop,restart,freeze,unfreeze} ...

* \-h | --help : Show this help message and exit

#### Subaction:&#x20;

{start,stop,restart,freeze,unfreeze}

* start : start container
* stop : stop container
* restart : restart container
* freeze : freeze container
* unfreeze : unfreeze container


## Session Options

usage: waydroid session \[-h] {start,stop} ...

* \-h | --help : Show this help message and exit

#### Subaction:&#x20;

* {start,stop} : start start session stop start session

## Examples

*   log:

    ```bash
    waydroid log > ~/waydroid-log.txt
    ```
*   logcat:

    ```bash
    sudo waydroid logcat > ~/waydroid-logcat.tx
    ```
*   Init for test builds:\
    Create the folder: `usr/share/waydroid-extra/images` and extract your customized images there.\
    First, you need to do a little cleanup (if this fails, reboot and try again):

    ```bash
    sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid
    ```

    Then run:

    ```bash
    sudo waydroid init -f
    sudo waydroid init
    ```

    Or, if you have your test images in another location (ex: \~/Downloads/test\_build/), then run:

    ```bash
    sudo waydroid init -f
    sudo waydroid init -i ~/Downloads/test_build
    ```
