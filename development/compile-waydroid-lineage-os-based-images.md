# Compile Waydroid - Lineage OS based images

## Getting started

To get started with Android/LineageOS, you'll need to get familiar with [Repo](https://source.android.com/source/using-repo.html) and [Version Control with Git](https://source.android.com/source/version-control.html).

To initialize your local repository using the LineageOS trees, use a command like this:

```text
repo init -u git://github.com/LineageOS/android.git -b lineage-17.1
```

Then to sync up:

```text
repo sync
```

After sync is complete, add the Waydroid vendor:

```text
git clone https://github.com/waydroid/android_vendor_waydroid vendor/extra
```

Then we setup the local build environment:

```text
. build/envsetup.sh
```

Next we generate the manifest:

```text
waydroid-generate-manifest
```

Then sync up again:

```text
repo sync
```

After sync is complete, we apply the Waydroid patches:

```text
apply-waydroid-patches
```

## How to build

Please see the [LineageOS Wiki](https://wiki.lineageos.org/) for building environment setup.

To build Waydroid:

```text
. build/envsetup.sh
lunch lineage_anbox_arm64-userdebug
make systemimage -j$(nproc --all)
make vendorimage -j$(nproc --all)
```

