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
<br>**EDIT**: I am now using Arch Linux and it works fine also on it. The procedure is slightly different though (no need to create deb packages).

- Download the latest Skylake GuC from [here](https://01.org/linuxgraphics/downloads/skylake-guc-6.1){:target="_blank"};
- Download the linux-firmware sources with `apt source linux-firmware`;
- Unpack the file sklgucver61.tar.bz2 and copy the firmware to the proper folder: `cp /tmp/skl_guc_ver6_1/skl_guc_ver6_1.bin ~/linux-firmware-1.157/i915`;
- Create the needed symlink with `ln -s ~/linux-firmware-1.157/skl_guc_ver6_1.bin ~/linux-firmware-1.157/skl_guc_ver6.bin`;
- Edit the `debian/changelog` file and either increase the version number to `1.158` or change the version number `1.157` to `1.157-0ubuntu1`;
- Create the package with `dpkg-buildpackage -us -uc`;
- Install the new package

After the new linux-firmware package has been installed, verify that the new firmware blob and its symlink are present inside the folder `/lib/firmware/i915`. If they are, it is now time to change the kernel sources to use the newest firmware.

- Install the needed tools with `sudo apt install build-essentials dh-autoreconf gawk debhelper`;
- Download the kernel sources with `apt source linux-image-$(uname -r)`;
- Edit the files `linux-image-$(uname -r)/drivers/gpu/drm/i915/intel_guc_loader.c` and `linux-image-$(uname -r)/ubuntu/i915/intel_guc_loader.c` and change:
	- `#define I915_SKL_GUC_UCODE "i915/skl_guc_ver4.bin"` to `#define I915_SKL_GUC_UCODE "i915/skl_guc_ver6.bin"`;
	- around line 588:
		{% highlight c %}
		else if (IS_SKYLAKE(dev)) {
			fw_path = I915_SKL_GUC_UCODE;
			guc_fw->guc_fw_major_wanted = 4;
			guc_fw->guc_fw_minor_wanted = 3;
		}
		{% endhighlight %}
		{% highlight c %}
		else if (IS_SKYLAKE(dev)) {
			fw_path = I915_SKL_GUC_UCODE;
			guc_fw->guc_fw_major_wanted = 6;
			guc_fw->guc_fw_minor_wanted = 0;
		}
		{% endhighlight %}
- Edit the files `debian/changelog` and `debian.master/changelog` and increase the version number from `4.4.0-18.34` to `4.4.0-18.35`;
- Recreate the package with `DEB_BUILD_OPTIONS=parallel=X AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic` where X is the number of CPU cores available on your system;
- Install the new packages;
- Verify if the new Skylake firmware is inside the initramfs with `lsinitramfs /boot/initrd.img-$(uname -r) | grep skl`
