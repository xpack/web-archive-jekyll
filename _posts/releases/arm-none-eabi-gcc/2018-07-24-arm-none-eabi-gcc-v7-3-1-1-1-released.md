---
title:  GNU MCU Eclipse ARM Embedded GCC v7.3.1-1.1 released
sidebar: arm-none-eabi-gcc

summary: "Version **7.3.1-1.1** is a new release of **GNU MCU Eclipse ARM Embedded GCC**."
app_name: "GNU MCU Eclipse ARM Embedded GCC"

download_url: https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/v7.3.1-1.1/

date: 2018-07-24 12:09:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2018/07/24/arm-none-eabi-gcc-v7-3-1-1-1-released/

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

---

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Compliance

This release follows the official
[GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm)
**7-2018-q2-update** release from June 27, 2018 and it is based on the
`gcc-arm-none-eabi-7-2018-q2-update-src.tar.bz2` source invariant.

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

* due to some changes in newlib, the definition of the `_EXFUN` macro changed
and the semihosting projects fail to build with a compile error in
`system/src/newlib/_syscalls.c`. The problem is in the project template, and
a fix will be available in the next release of GNU MCU Eclipse plug-ins
[#317](https://github.com/gnu-mcu-eclipse/eclipse-plugins/issues/317).


## Checksums

The SHA-256 hashes for the files are:

```txt
ecb558466dc75ed61ec6bf223eceea726a03d4a647577e04991820a4d96415cc ?
gnu-mcu-eclipse-arm-none-eabi-gcc-7.3.1-1.1-20180724-0637-centos32.tgz

d521ec54ac79e7abcdf1a88b7e74cea2155e355e9b3d2eacaa915c5827687af3 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-7.3.1-1.1-20180724-0637-centos64.tgz

0e6d07f8c01cd95d1ac0f19a4e362d0598ad879cc6a22da02809f4d9249b9dc1 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-7.3.1-1.1-20180724-0637-macos.tgz

c742d58e498928e5209d905d33c1778e7fb482d87ce7e1b214334d2313e51bf7 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-7.3.1-1.1-20180724-0637-win32.zip

92cebc992bea624f19f17246bd496b35db1d8dccf4baa1b7f786f2b6e2c3b17d ?
gnu-mcu-eclipse-arm-none-eabi-gcc-7.3.1-1.1-20180724-0637-win64.zip
```
