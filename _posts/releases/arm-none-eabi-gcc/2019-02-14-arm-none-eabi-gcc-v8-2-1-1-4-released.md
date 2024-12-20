---
title:  GNU MCU Eclipse ARM Embedded GCC v8.2.1-1.4 released
sidebar: arm-none-eabi-gcc

summary: "Version **8.2.1-1.4** is a maintenance release of **GNU MCU Eclipse ARM Embedded GCC** that fixes the bugs affecting Windows LTO builds, present in the previous release."
app_name: "GNU MCU Eclipse ARM Embedded GCC"

download_url: https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/tag/v8.2.1-1.4/

date: 2019-02-14 10:48:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2019/02/14/arm-none-eabi-gcc-v8-2-1-1-4-released/

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

- a patch was applied to binutils to fix the 32-bit objcopy bug
  [24065](https://sourceware.org/bugzilla/show_bug.cgi?id=24065)
- GDB was built the Git commit ad0f979c9 from 2019-01-29, to fix the bugs
  affecting C++ LTO projects
  [24145](https://sourceware.org/bugzilla/show_bug.cgi?id=24145)
- [Issue:[#3](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/issues/3)]
  by default, the GCC build script fails to create `liblto_plugin-0.dll`
  for static builds with mingw; code to create the plugin was added
- [Issue:[#1](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/issues/1)]
  the `liblto_plugin` copied/linked to the `lib/bdf-plugins` for `ar`
  to find it and be able to process archives with LTO objects
- a patch was applied to gcc to fix the Windows LTO with -g bug
  [89183](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=89183)
- a patch was applied to gcc to fix the Windows paths with spaces bug
  [89249](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=89249)

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

* LTO is still not functional on Windows.

## Checksums

The SHA-256 hashes for the files are:

```txt
4d45ca08ba613f0f7d3ffe908adf3374c284216d39b31cb91fd9248a3f0f26e1 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.4-20190214-0604-centos32.tgz

41277cb5fd2107f2f5b273d04ec2d9f2d923caf25e14a80e4fbea9de5a5f07e1 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.4-20190214-0604-centos64.tgz

845274a50fa7b0c6e4af7641ece4aba33c1fec447cb32537f68fda389998a6af ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.4-20190214-0604-macos.tgz

f9f517082540f13e0803ac8eaf64a7f3a8c54bfc5b5ad4e6589c31e2289d617e ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.4-20190214-0604-win32.zip

fbdbdf46ca35201bc3330eda659b3aeb8f77003ebc26e930c1f2535429e0e3be ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.4-20190214-0604-win64.zip
```
