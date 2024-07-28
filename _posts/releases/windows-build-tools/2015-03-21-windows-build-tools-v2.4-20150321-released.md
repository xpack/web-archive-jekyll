---
title:  GNU ARM Eclipse Windows Build Tools v2.4-20150321* released
sidebar: windows-build-tools

download_url: https://github.com/gnu-mcu-eclipse/windows-build-tools/releases/tag/v2.4/
date: 2015-03-21 12:00:00 +0200

comments: true

categories:
  - releases
  - windows-build-tools

tags:
  - releases
  - windows-build-tools
  - windows
  - setup
  - build
  - make
  - rm
  - busybox

---

Version 2.4-201503212005 is a new release of the GNU ARM Eclipse Windows Build Tools.

[Binary files »]({{ page.download_url }})

## Improvements

The GNU ARM Eclipse Windows Build Tools v2.4 package includes the **version 4.1 of GNU make** (built from MSYS2 source files), and version **1.24.0-git of BusyBox**, which provides a convenient implementation for sh/rm/echo.

In addition to using the most recent versions, the new packages install in separate folders for each version, allowing multiple versions to coexist.

Apart from v2.3 where a binary version of BusyBox was packed, in version v2.4 BusyBox is also compiled from sources, so the entire package is freshly build from sources.

The managed build plug-in generally auto-detects the latest build tools version, by using the Windows registry keys or by searching several designated folders, and defaults to using it. If you need to use a different version, update the **Global Tools Paths** (or **Workspace Tools Paths**) in C/C++ → Build preferences.

Please note that it is no longer required to manually update the environment PATH, if properly set in the preferences page (as **Build tools folder**), the plug-in automatically updates the PATH.

## Known problems

* the uninstall script has a problem and erroneously removes some registry keys and folders. **DO NOT run the uninstall.exe** since you might damage your system; instead, install the new version on top of it.

## Download

The new Windows Build Tools can be downloaded from the [GitHub Release]({{ page.download_url }}) page.

The available files are:

	gnuarmeclipse-build-tools-win32-2.4-201503212005-setup.exe
