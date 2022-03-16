# Waydroid command line options

Waydroid offers a number of command line arguments and options in order to work with the various parts of the program.

## Usage

`waydroid [-h] [-V] [-l LOG] [--details-to-stdout] [-v] [-q]`

## optional arguments

* `-h`, `--help` : Show this help message and exit
* `-V`, `--version` : Show program's version number and exit
* `-l LOG`, `--log LOG` : Path to log file (default: /var/lib/waydroid)
* `--details-to-stdout` : Print details (e.g. build output) to stdout, instead of writing to the log
* `-v`, `--verbose` : Write even more to the logfiles (this may reduce performance)
* `-q`, `--quiet` : Do not output any log messages
* `-f` : Force options (used with init commands)
* `-i LOCATION` : Initialize from specified location (default: `/usr/share/waydroid-extra/images`) _\*used with init action\*_

## Actions

You can use the following actions with the waydroid tool

* `status` : Quick check for the waydroid
* `log` : Follow the waydroid logfile
* `init` : Set up waydroid specific configs and install images
* `upgrade` : Upgrade images
* `session` : Session controller
* `container` : Container controller
* `app` : Applications controller (see: [Install and Run Android Applications](install-and-run-android-applications.md))
* `prop` : Android properties controller
* `show-full-ui` : Show android full screen in window
* `shell` : Run remote shell command
* `logcat` : Show Android's logcat

## Init Options

Usage: `waydroid init [-h] [-i IMAGES_PATH] [-f] [-c SYSTEM_CHANNEL] [-v VENDOR_CHANNEL] [-r ROM_TYPE] [-s SYSTEM_TYPE]`

* `-h` | `--help` : Show this help message and exit
* `-i IMAGES_PATH` | `--images_path IMAGES_PATH` : Custom path to waydroid images (default in /var/lib/waydroid/images)
* `-f` | `--force` : Used when resetting or using custom images added to /usr/share/waydroid-extra/images
* `-c SYSTEM_CHANNEL` | `--system_channel SYSTEM_CHANNEL` : Custom system channel (options: OTA channel URL; default is Official OTA server)
* `-v VENDOR_CHANNEL` | `--vendor_channel VENDOR_CHANNEL` : Custom vendor channel (options: OTA channel URL; default is Official OTA server)
* `-r ROM_TYPE` | `--rom_type ROM_TYPE` : Rom type (options: "lineage", "bliss" or OTA channel URL; default is LineageOS)
* `-s SYSTEM_TYPE` | `--system_type SYSTEM_TYPE` : System type (options: VANILLA, FOSS or GAPPS; default is VANILLA)

## Log Options

Usage: `waydroid log [-h] [-n LINES] [-c]`

* `-h` | `--help` : Show this help message and exit
* `-n LINES` | `--lines LINES` : Count of initial output lines
* `-c` | `--clear` : Clear the log

## Container Options

Usage: `waydroid container [-h] {start,stop,restart,freeze,unfreeze} ...`

* `-h` | `--help` : Show this help message and exit

#### Subaction:&#x20;

`{start,stop,restart,freeze,unfreeze}`

* `start` : start container
* `stop` : stop container
* `restart` : restart container
* `freeze` : freeze container
* `unfreeze` : unfreeze container


## Session Options

Usage: `waydroid session [-h] {start,stop} ...`

* `-h` | `--help` : Show this help message and exit

#### Subaction:&#x20;

* `{start,stop}` : start start session stop start session

## Examples

*   `log`:

    ```bash
    waydroid log > ~/waydroid-log.txt
    ```
*   `logcat`:

    ```bash
    sudo waydroid logcat > ~/waydroid-logcat.tx
    ```
*   Initialize for test builds:\
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
