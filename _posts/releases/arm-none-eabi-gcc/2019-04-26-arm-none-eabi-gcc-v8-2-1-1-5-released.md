---
title:  GNU MCU Eclipse ARM Embedded GCC v8.2.1-1.5 released
sidebar: arm-none-eabi-gcc

summary: "Version **8.2.1-1.5** is a maintenance release of **GNU MCU Eclipse ARM Embedded GCC** that fixes the bugs affecting Windows LTO builds, present in the previous release."
app_name: "GNU MCU Eclipse ARM Embedded GCC"

download_url: https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/tag/v8.2.1-1.5/

date: 2019-04-26 23:43:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2019/04/26/arm-none-eabi-gcc-v8-2-1-1-5-released/

comments: true

categories:
  - releases
  - arm-none-eabi-gcc

tags:
  - releases
  - arm
  - arm-none-eabi-gcc
  - gcc
  - binaries
  - lto

---

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Deprecated

Use v8.2.1-1.6.

## Compliance

This release follows the official
[GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm)
**8-2018-q4-major** release from December 20, 2018 and it is based on the
`gcc-arm-none-eabi-8-2018-q4-major-src.tar.bz2` source invariant.

## Changes

Compared to the ARM distribution, the build procedure is more or less the
same and there should be no functional differences, except the following
bug fixes:

- [Issue:[#3](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/issues/3)]
  due to a problem in the GCC configure script and the specifics of the static
  build, LTO was not effective on Windows, and the initial workaround proved
  not effective either; in the new build environment the configure script is
  enables LTO and it is functional on windows too;
- a patch was applied to binutils to fix the 32-bit objcopy bug
  [24065](https://sourceware.org/bugzilla/show_bug.cgi?id=24065)
- GDB was built the Git commit ad0f979c9 from 2019-01-29, to fix the bugs
  affecting C++ LTO projects
  [24145](https://sourceware.org/bugzilla/show_bug.cgi?id=24145)
- [Issue:[#3](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/issues/3)]
  by default, the GCC build script fails to create `liblto_plugin-0.dll`
  for static builds with mingw; builds are now using shared libraries
- [Issue:[#1](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/issues/1)]
  the `liblto_plugin` copied/linked to the `lib/bdf-plugins` for `ar`
  to find it and be able to process archives with LTO objects
- a patch was applied to gcc to fix the Windows LTO with -g bug
  [89183](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=89183)
- a patch was applied to gcc to fix the Windows paths with spaces bug
  [89249](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=89249)

## Python 3

Experimental support was added for Python 3 in GDB. Unfortunately compiling
GDB with mingw-w64 requires an update to the new Python 3
API, not yet available at the moment of this release.

Also support for 32-bit machines might not be fully functional.

## Binaries

Binaries for **Windows**, **macOS** and **GNU/Linux** are provided.

The GNU/Linux binaries were built on two CentOS 6 Docker images (32/64-bit),
and run on any distribution based on CentOS 6 or later.

The macOS binary was built on a macOS 10.10.5 and must run on any newer
macOS system.

The Windows binaries were built with mingw-w64, and run on any reasonably
recent **i686** and **x86_64** Windows machines.

Instructions on how to install the binaries are available in the separate [How to install the ARM toolchain?]({{ site.baseurl }}/dev-tools/arm-none-eabi-gcc/install/) page.

The toolchain is also available as an
[xPack](https://www.npmjs.com/package/@gnu-mcu-eclipse/arm-none-eabi-gcc)
and can be conveniently installed with
[`xpm`](https://www.npmjs.com/package/xpm):

```sh
xpm install --global @gnu-mcu-eclipse/arm-none-eabi-gcc@latest
```

This installs the latest available version.

For better control and repeatability, the build scripts use Docker containers;
all files required during builds are available as a separate
[gnu-mcu-eclipse/arm-none-eabi-gcc-build](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build)
project.

## Known problems

### Windows paths with spaces

Installing the toolchain in locations which use spaces in the path is still problematic.

Temporarily move the toolchain to paths which do not use spaces, or, even better, install it via `xpm`, which uses safe paths.

## Checksums

The SHA-256 hashes for the files are:

```txt
63f959858a1a1907797ea7f17e20048d559281f77c3742015617ebff2e71a501
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.5-20190426-0353-centos32.tgz

a42eb8e5be1979e5e73d2d3c3832e617fc7415387aa47cc8c3eb197b12e2d38c
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.5-20190426-0353-centos64.tgz

8d56318b51508adffceb7f62829a93136021c1f49357c94fc82046824213620d
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.5-20190426-0353-macos.tgz

a953c13529df786c6d52d978f31a60e75275a2830fe5e24bc908b6665d9badc8
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.5-20190426-0353-win32.zip

f62649688c1e68d0fcb2eea126688cbeae9e1b7b24a8e81afefe8519d45b7680
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.5-20190426-0353-win64.zip
```
