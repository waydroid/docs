# Manual Patch Resolution

At the end of [the `apply-waydroid-patches` script](https://github.com/waydroid/android_vendor_waydroid/blob/b2fa4643f50488eefcfd415290bcfa445752e8c9/vendorsetup.sh#L4), it will show the results of how each patch applied. You will want to then make a copy of all the results of the patch scripts \(Copy and paste the contents of the terminal output into a Notepad or text document\). Each of the patches applied either resulted in "Applying", "Already applied", or "Conflicts". The only ones we want to pay attention to here are the "Conflicts", but only half of them.

Some of the patches have duplicates for different vendor setups. So you will sometimes get results that look like this:

```text
Conflicts          system/core/0015-init-don-t-bail-out-even-no-SELinux-domain-defined.patch
Applying          system/core/0015-init-don-t-bail-out-even-no-SELinux-domain-defined.patch 0
```

Notice how the one starting with "0015-" failed, but the patch resolution it found was applied correctly? If that happened on your vendor setup, you can ignore that patch. But if you only see one patch that had a "Conflicts", that will need to be applied and fixed.

First, you apply the patch manually:

```text
git am "<SOURCES_ROOT>/vendor/extra/waydroid-patches/base-patches-<AOSP_SDK_VERSION>/<PATCH_PATH>"
```

You can expect that to fail, but it's crucial to the next step. Next you patch the file again, but using the "patch" command

```text
patch -p1 < "<SOURCES_ROOT>/vendor/extra/waydroid-patches/base-patches-<AOSP_SDK_VERSION>/<PATCH_PATH>"
```

This will generate the .orig & .rej files to help narrow down what you need to fix. Once the conflicting parts \(what's in the .rej files\) are resolved, delete the .rej & .orig files, then stage the files:

```text
git add -A
```

Then we can continue the staged git am commit from the first step:

```text
git am --continue
```

After applying the patch\(s\) to your local project folder, remember to generate the patch needed to resolve that conflict:

```text
git format-patch -1
```

Then copy the patch to the appropriate vendor folder for the conflict. Any conflicts that happened from the base patches themselves should go to the vendor/extra/waydroid-patches/roms-patches/your-rom-name/ folder Example:

```text
cp system/core/0001-init-don-t-bail-out-even-no-SELinux-domain-defined.patch vendor/extra/waydroid-patches/roms-patches/__YourRomName__/system/core/0015-init-don-t-bail-out-even-no-SELinux-domain-defined.patch
```

