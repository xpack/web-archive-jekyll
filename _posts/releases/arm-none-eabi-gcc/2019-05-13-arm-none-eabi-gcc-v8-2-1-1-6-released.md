---
title:  GNU MCU Eclipse ARM Embedded GCC v8.2.1-1.6 released
sidebar: arm-none-eabi-gcc

summary: "Version **8.2.1-1.6** is a maintenance release of **GNU MCU Eclipse ARM Embedded GCC** that (finally) fixes the bugs affecting Windows LTO builds, present in the previous release."
app_name: "GNU MCU Eclipse ARM Embedded GCC"

download_url: https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/tag/v8.2.1-1.6/

date: 2019-05-10 06:05:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2019/05/13/arm-none-eabi-gcc-v8-2-1-1-6-released/

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

## Compliance

This release follows the official
[GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm)
**8-2018-q4-major** release from December 20, 2018 and it is based on the
`gcc-arm-none-eabi-8-2018-q4-major-src.tar.bz2` source invariant,
which include GCC 8.2.1. GDB was built with the latest available
sources (8.3.50).

## Changes

Compared to the ARM distribution, the build procedure is more or less the
same and there should be no functional differences, except the following
bug fixes:

- [Issue:[#4](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/issues/4)]
  the Windows paths with spaces bug apparently was caused by an old version of
  and with the new version (5.0.4) the
  [89249](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=89249)
  `gcc.c` patch is no longer needed;
- [Issue:[#3](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/issues/3)]
  due to a problem in the GCC configure script and the specifics of the static
  build, LTO was not effective on Windows, and the initial workaround proved
  not effective either; in the new build environment the configure script is
  enables LTO and it is functional on windows too;
- [Issue:[#1](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/issues/1)]
  the `liblto_plugin` copied/linked to the `lib/bdf-plugins` for `ar`
  to find it and be able to process archives with LTO objects
- a patch was applied to binutils to fix the 32-bit objcopy bug
  [24065](https://sourceware.org/bugzilla/show_bug.cgi?id=24065)
- a patch was applied to gcc to fix the Windows LTO with -g bug
  [89183](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=89183)

Due to a large number of fixes needed, GDB was built with the
latest Git commit bda678b9 from 2019-05-09,
corresponding to GDB 8.3.50, to fix
the bugs affecting C++ LTO projects
[24145](https://sourceware.org/bugzilla/show_bug.cgi?id=24145).

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

## Tests

The binaries were testes on Windows 10 Pro 32/64-bit, Ubuntu 18 LTS 64-bit,
Xubuntu 18 LTS 32-bit and macOS 10.13.

The tests consist in building and debugging some
[simple Eclipse projects](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build/tree/master/tests/eclipse)
available in the build project.

Since the source code used for GCC is identical to the one used by ARM, the
long and complex tests performed by ARM to validate their release were not
executed again.

## Known problems

### Illegal links in `libexec` for GNU/Linux

Although the current release is fully functional, due to a problem with
the GCC make, the build created links with illegal names in the `libexec`
folders. The current code used to unpack the archives does not complain,
but future versions may include more thorough checks and fail. A new
release to fix this issue will be available soon.

## Checksums

The SHA-256 hashes for the files are:

```txt
a4fc37f897ff50a3e3807e87db60ccb0844f37eb618f0935ece94a581fd98eec
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.6-20190510-1829-centos32.tgz

e85df3bdc9b8e9c91e00924feb6f7f9909c94af08bd7e097d4ab857e0facc316
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.6-20190510-1829-centos64.tgz

63cdda07c539d2a43df89d7ec17b2ab4119ebfe4a5c46295c2bc1821755b093b
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.6-20190510-1829-macos.tgz

780cda157454dd073132c52aa46f2d43b1f325a1f38a82c3283de76492899fb1
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.6-20190510-1829-win32.zip

a88823b4cbb9e060975f14e1e839eace1cf0cb26386f99d52e692b15455ec3dd
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.6-20190510-1829-win64.zip
```
