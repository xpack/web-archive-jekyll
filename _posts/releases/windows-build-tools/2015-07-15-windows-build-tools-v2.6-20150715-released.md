---
title:  GNU ARM Eclipse Windows Build Tools v2.6-20150715* released
sidebar: windows-build-tools

summary: "Version **v2.6-201507152002** is a new release of the GNU ARM Eclipse Windows Build Tools, adding support for Windows 64-bit."
app_name: "GNU ARM Eclipse Windows Build Tools"

download_url: https://github.com/gnu-mcu-eclipse/windows-build-tools/releases/tag/v2.6/
date: 2015-07-15 12:00:00 +0300

# redirect_to: https://xpack-dev-tools.github.io/windows-build-tools-xpack/blog/2015/07/15/windows-build-tools-v2.6-20150715-released/

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

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Improvements

The GNU ARM Eclipse Build Tools v2.6 package includes the **version 4.1 of GNU make** (built from MSYS2 source files), and version **1.24.0-git of BusyBox**, which provides a convenient implementation for sh/rm/echo.

The main change from v2.4 is a patch that allows BusyBox to run correctly on 64-bit Windows systems. Apparently this not only makes usage safer, by avoiding the DLL32 mess, but also slightly improves build performances.

## Known problems

* none so far

## Checksums

The MD5 sums of the files are:

```txt
d52c5c3bedc8b34acdcb8384d8b2cfc3
gnuarmeclipse-build-tools-win32-2.6-201507152002-setup.exe

a47b0a38355ee9449cb3930beb303762
gnuarmeclipse-build-tools-win64-2.6-201507152002-setup.exe
```
