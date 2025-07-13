# Compile Waydroid - Lineage OS based images

## Getting started

To get started with Android/LineageOS, you'll need to get familiar with [Repo](https://source.android.com/source/using-repo.html) and its [Git workflow](https://source.android.com/docs/setup/create/coding-tasks).

### Initializing

To initialize your local repository using the LineageOS trees, use a command like this:

```text
repo init -u https://github.com/LineageOS/android.git -b lineage-20.0 --git-lfs
repo sync build/make
```

Then we grab the Waydroid local\_manifests

```text
wget -O - https://raw.githubusercontent.com/waydroid/android_vendor_waydroid/lineage-18.1/manifest_scripts/generate-manifest.sh | bash
```

### Syncing

Then to sync up:

```text
repo sync
```

Then we setup the local build environment:

```text
. build/envsetup.sh
```

### Patching

After that is complete, we apply the Waydroid patches:

```text
apply-waydroid-patches
```

## How to build

Please see the [LineageOS Wiki](https://wiki.lineageos.org/) for building environment setup.

### Waydroid AOSP Lunch Options:

```text
lineage_waydroid_arm-userdebug
lineage_waydroid_arm64-userdebug
lineage_waydroid_x86-userdebug
lineage_waydroid_x86_64-userdebug
```

### Waydroid Build Commands:

```text
. build/envsetup.sh
lunch lineage_waydroid_arm64-userdebug
make systemimage -j$(nproc --all)
make vendorimage -j$(nproc --all)
```
### Image Generation From Sparse Image:

The output of the AOSP build system is an "Android Sparse Image"; we need raw fileystems instead.
Starting from the `lineage-20.0` branch, the output is already a raw image.

On earlier branches, from the same terminal where you just built a system and a vendor image, run:

```text
simg2img $OUT/system.img ~/system.img
simg2img $OUT/vendor.img ~/vendor.img
```

to obtain your target raw images at ~/system.img and ~/vendor.img

### HALIUM images

The official Waydroid OTA channels provide special vendor images for HALIUM systems.
These are regular vendor images that are stripped of the Mesa GPU drivers in order to save space.
To build a HALIUM image the same way as the official images, simply disable the `TARGET_USE_MESA` option before compiling:

```text
export TARGET_USE_MESA=false
```

## Troubleshooting

### Local Manifest:

To manually regenerate the local\_manifests, we also have added a function to do so

```text
waydroid-generate-manifest
```

After doing that you will want to resync \(this will wipe out any local changes, so make sure you save your work to a different branch\)

### Patch Conflicts:

See [Manual Patch Resolution](manual-patch-resolution.md)

