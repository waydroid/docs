# Compile Waydroid - Lineage OS based images

## Getting started

To get started with Android/LineageOS, you'll need to get familiar with [Repo](https://source.android.com/source/using-repo.html) and its [Git workflow](https://source.android.com/docs/setup/create/coding-tasks).

### Initializing

To initialize your local repository using the LineageOS trees, use a command like this:

```text
repo init -u https://github.com/LineageOS/android.git -b lineage-18.1 --git-lfs
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

Make sure simg2img is installed and:

```text
simg2img system.img output_dir/system.img
simg2img vendor.img output_dir/vendor.img
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

