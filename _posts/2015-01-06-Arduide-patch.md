---
comments: true
date: 2015-01-06
layout: blog
category: blog
title: 'Arduide and SDK v1.0.6'
summary: 'This patch allows Arduide to correctly recognize the Arduino SDK v1.0.6'
image: /images/header_images/arduino.png
tags: [arduino,arduide,patch]
---

[Arduide](http://mupuf.org/project/arduide.html) is a Qt-based IDE for the open-source Arduino electronics prototyping platform.

The current [git](https://gitorious.org/arduide) version (11/01/2014) doesn't correctly recognize the 1.0.6 SDK.

If you need to execute Arduide against the 1.0.6 SDK, you need to patch the sources using [this patch](attachments/arduide-add-sdk106.patch).

The following is the code of the abovementioned patch:

	diff -ru arduide/CMakeLists.txt arduide-patched/CMakeLists.txt
	--- arduide/CMakeLists.txt	2014-12-23 10:05:46.549755208 +0100
	+++ arduide-patched/CMakeLists.txt	2014-12-23 10:01:29.135266754 +0100
	@@ -29,7 +29,7 @@
	 
	 # Compatible version of the Arduino SDK (don't forget to update Toolkit.h)
	 set(ARDUINO_SDK_VERSION "105")
	-set(ARDUINO_SDK_VERSION_NAME "1.0.5")
	+set(ARDUINO_SDK_VERSION_NAME "1.0.6")
	 add_definitions(-DARDUINO_SDK_VERSION="${ARDUINO_SDK_VERSION}")
	 add_definitions(-DARDUINO_SDK_VERSION_NAME="${ARDUINO_SDK_VERSION_NAME}")
	 
	diff -ru arduide/env/Toolkit.cpp arduide-patched/env/Toolkit.cpp
	--- arduide/env/Toolkit.cpp	2014-12-23 10:05:46.553088597 +0100
	+++ arduide-patched/env/Toolkit.cpp	2014-12-23 10:02:42.389981275 +0100
	@@ -143,7 +143,7 @@
	 {
		 QString version = toolkitVersion(path);
	 
	-    return version == "1.0.5" || version == "1.0.4" || version == "1.0.3" || version == "1.0.2" || version == "1.0.1" || version == "1.0" || version == "0023";
	+    return version == "1.0.6" || version == "1.0.5" || version == "1.0.4" || version == "1.0.3" || version == "1.0.2" || version == "1.0.1" || version == "1.0" || version == "0023";
	 }
	 
	 QString Toolkit::avrPath()
	diff -ru arduide/gui/FirstTimeWizard.ui arduide-patched/gui/FirstTimeWizard.ui
	--- arduide/gui/FirstTimeWizard.ui	2014-12-23 10:05:46.553088597 +0100
	+++ arduide-patched/gui/FirstTimeWizard.ui	2014-12-23 10:01:52.315721398 +0100
	@@ -37,7 +37,7 @@
		 <item>
		  <widget class="QRadioButton" name="existingInstallButton">
		   <property name="text">
	-       <string>Existing installation (Arduino SDK 0023, 1.0, 1.0.1 to 1.0.5)</string>
	+       <string>Existing installation (Arduino SDK 0023, 1.0, 1.0.1 to 1.0.6)</string>
		   </property>
		  </widget>
		 </item>
	@@ -92,7 +92,7 @@
		 <item>
		  <widget class="QRadioButton" name="automaticInstallButton">
		   <property name="text">
	-       <string>Automatic installation (Arduino SDK 1.0.5)</string>
	+       <string>Automatic installation (Arduino SDK 1.0.6)</string>
		   </property>
		  </widget>
		 </item>
