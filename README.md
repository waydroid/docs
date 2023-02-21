# Waydroid

Waydroid is a container-based approach to boot a full Android system on a regular GNU/Linux system like Ubuntu.

## Overview

Waydroid uses Linux namespaces (user, pid, uts, net, mount, ipc) to run a full Android system in a container and provide Android applications on any GNU/Linux-based platform.

The Android inside the container has direct access to needed hardwares.

The Android runtime environment ships with a minimal customized Android system image based on the [LineageOS](https://lineageos.org). The used image is currently based on Android 10

## Index

### Usage

{% content-ref url="usage/install-on-desktops.md" %}
[install-on-desktops.md](usage/install-on-desktops.md)
{% endcontent-ref %}

{% content-ref url="usage/install-and-run-android-applications.md" %}
[install-and-run-android-applications.md](usage/install-and-run-android-applications.md)
{% endcontent-ref %}

{% content-ref url="usage/waydroid-command-line-options.md" %}
[waydroid-command-line-options.md](usage/waydroid-command-line-options.md)
{% endcontent-ref %}

{% content-ref url="usage/waydroid-prop-options.md" %}
[waydroid-prop-options.md](usage/waydroid-prop-options.md)
{% endcontent-ref %}

### FAQ

{% content-ref url="faq/google-play-certification.md" %}
[google-play-certification.md](faq/google-play-certification.md)
{% endcontent-ref %}

{% content-ref url="faq/disable-on-screen-keyboard.md" %}
[disable-on-screen-keyboard.md](faq/disable-on-screen-keyboard.md)
{% endcontent-ref %}

{% content-ref url="faq/community-projects-we-like.md" %}
[community-projects-we-like.md](faq/community-projects-we-like.md)
{% endcontent-ref %}

{% content-ref url="faq/get-waydroid-to-work-through-a-vm.md" %}
[get-waydroid-to-work-through-a-vm.md](faq/get-waydroid-to-work-through-a-vm.md)
{% endcontent-ref %}

{% content-ref url="faq/using-adb-with-waydroid.md" %}
[using-adb-with-waydroid.md](faq/using-adb-with-waydroid.md)
{% endcontent-ref %}

{% content-ref url="faq/setting-up-waydroid-only-sessions.md" %}
[setting-up-waydroid-only-sessions.md](faq/setting-up-waydroid-only-sessions.md)
{% endcontent-ref %}

{% content-ref url="faq/setting-up-a-shared-folder.md" %}
[setting-up-a-shared-folder.md](faq/setting-up-a-shared-folder.md)
{% endcontent-ref %}

{% content-ref url="faq/color-correction-in-mutter.md" %}
[color-correction-in-mutter.md](faq/color-correction-in-mutter.md)
{% endcontent-ref %}

{% content-ref url="faq/backup-restore-apps-and-data.md" %}
[backup-restore-apps-and-data.md](faq/backup-restore-apps-and-data.md)
{% endcontent-ref %}

{% content-ref url="faq/using-custom-waydroid-images.md" %}
[using-custom-waydroid-images.md](faq/using-custom-waydroid-images.md)
{% endcontent-ref %}

### Development:

{% content-ref url="development/compile-waydroid-lineage-os-based-images.md" %}
[compile-waydroid-lineage-os-based-images.md](development/compile-waydroid-lineage-os-based-images.md)
{% endcontent-ref %}

{% content-ref url="development/manual-patch-resolution.md" %}
[manual-patch-resolution.md](development/manual-patch-resolution.md)
{% endcontent-ref %}

## Reporting bugs

If you have found an issue with Waydroid, please [file a bug](https://github.com/waydroid/waydroid/issues/new/choose).

## Get in Touch

If you want to get in contact with the developers please feel free to join the _Waydroid_ groups in 
- [Matrix](https://matrix.to/#/#waydroid:mrcyjanek.net) 
- [Telegram](https://t.me/WayDroid)
- [Reddit](https://www.reddit.com/r/waydroid/)

## Credits

We'd like to say thanks to all these great teams & projects: @Anbox @LineageOS @Android-x86 @spurv @LXC and many others, for you still lead the way for Open Innovation in Linux and the Android community.
