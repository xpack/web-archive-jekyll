---

title:  GNU MCU Eclipse Windows Build Tools v2.11-20180428 released
sidebar: windows-build-tools

summary: "Version **2.11-20180428** is a maintenance release of the GNU MCU Eclipse Windows Build Tools."
app_name: "GNU MCU Eclipse Windows Build Tools"

download_url: https://github.com/gnu-mcu-eclipse/windows-build-tools/releases/tag/v2.11-20180428/

date: 2018-04-28 20:59:00 +0300

# redirect_to: https://xpack-dev-tools.github.io/windows-build-tools-xpack/blog/2018/04/28/windows-build-tools-v2-11-20180428-released/

comments: true

categories:
  - releases
  - windows-build-tools

comments: true

categories:
  - releases
  - windows-build-tools

tags:
  - releases
  - windows-build-tools
  - windows
  - build
  - make
  - rm
  - mkdir
  - busybox

---

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

Separate archive files are provided for **Windows** (x64 and x86) systems.

{% include note.html content="By design, installing the xPack binaries does not require administrative rights, thus only portable archives are provided; Windows setups are no longer supported." %}

## Content

The GNU MCU Eclipse Build Tools v2.11 package includes the **version 4.2.1 of GNU make** (built from MSYS2 source files), and version **1.29.0-git of BusyBox**, which provides a convenient implementation for `sh`/`rm`/`echo`/`mkdir`.

## Changes

Both the make and BusyBox sources were upgraded to the latest available.

## Known problems

* none so far



## Checksums

The SHA-256 hashes for the files are:

```txt
810aabd776724ba54195807f0421932dab0809c15741a2076b8b6b1275463fd3 ?
gnu-mcu-eclipse-build-tools-2.11-20180428-1604-win32.zip

9995e4a15a4893ca4ccca1bccafcd9783cbac9a94ceedc59b3f11137d3e3b0f8 ?
gnu-mcu-eclipse-build-tools-2.11-20180428-1604-win64.zip
```
