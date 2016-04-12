---                                                                                     
comments: true
date: 2016-04-12
layout: post
title: 'Update Skylake GuC on Ubuntu'
subtitle: 'How to update Ubuntu to the latest Skylake GuC firmware'
---

As many of you already know, Skylake and other Intel CPUs now require [graphics firmware blobs](http://www.phoronix.com/scan.php?page=news_item&px=intel-skl-bxt-firmware-blobs){:target="_blank"} to properly run.<br>
Recently, a new major version of the GuC firmware for Skylake [came out](https://01.org/linuxgraphics/downloads/skylake-guc-6.1){:target="_blank"}. This firmware has already been included in the latest linux-firmware [git repository](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/commit/?id=0a0c97667d0e80c56de8fd999d17bf2b553aab8f){:target="_blank"} but, of course, not all the distros are updating this package on a regular basis.<br>Ubuntu is one of these distros, so I had to manually update both the linux-firmware and the kernel packages on my own. This was easy to achieve though :-)
<br>Currently, I am using Ubuntu GNOME 16.04 but it _should_ work also on the other flavors.

1. Download the latest Skylake GuC from [here](https://01.org/linuxgraphics/downloads/skylake-guc-6.1){:target="_blank"};
2. Download the linux-firmware sources with `apt source linux-firmware`;
3. Unpack the file sklgucver61.tar.bz2 and copy the firmware to the proper folder: `cp /tmp/skl_guc_ver6_1/skl_guc_ver6_1.bin ~/linux-firmware-1.157/i915`;
4. Create the needed symlink with `ln -s ~/linux-firmware-1.157/skl_guc_ver6_1.bin ~/linux-firmware-1.157/skl_guc_ver6.bin`;
5. Edit the `debian/changelog` file and either increase the version number to `1.158` or change the version number `1.157` to `1.157-0ubuntu1`;
6. Create the package with `dpkg-buildpackage -us -uc`;
7. Install the new package

After the new linux-firmware package has been installed, verify that the new firmware blob and its symlink are present inside the folder `/lib/firmware/i915`. If they are, it is now time to change the kernel sources to use the newest firmware.

1. Install the needed tools with `sudo apt install build-essentials dh-autoreconf gawk debhelper`;
2. Download the kernel sources with `apt source linux-image-$(uname -r)`;
3. Edit the files `linux-image-$(uname -r)/drivers/gpu/drm/i915/intel_guc_loader.c` and `linux-image-$(uname -r)/ubuntu/i915/intel_guc_loader.c` and change `#define I915_SKL_GUC_UCODE "i915/skl_guc_ver4.bin"` to `#define I915_SKL_GUC_UCODE "i915/skl_guc_ver6.bin"`;
4. Edit the files `debian/changelog` and `debian.master/changelog` and increase the version number from `4.4.0-18.34` to `4.4.0-18.35`;
5. Recreate the package with `DEB_BUILD_OPTIONS=parallel=X AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic` where X is the number of CPU cores available on your system;
6. Install the new packages;
7. Verify if the new Skylake firmware is inside the initramfs with `lsinitramfs /boot/initrd.img-$(uname -r) | grep skl`
