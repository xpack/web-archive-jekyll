---
title:  GNU MCU Eclipse ARM Embedded GCC v8.2.1-1.1 released
sidebar: arm-none-eabi-gcc

summary: "Version **8.2.1-1.1** is a new release of **GNU MCU Eclipse ARM Embedded GCC**."
app_name: "GNU MCU Eclipse ARM Embedded GCC"

download_url: https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/tag/v8.2.1-1.1/

date: 2019-01-03 20:39:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2019/01/03/arm-none-eabi-gcc-v8-2-1-1-1-released/

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

## Deprecated

Use v8.2.1-1.6.

## Compliance

This release follows the official
[GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm)
**8-2018-q4-major** release from December 20, 2018 and it is based on the
`gcc-arm-none-eabi-8-2018-q4-major-src.tar.bz2` source invariant.

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

The latest Binutils, also used in Arm Embedded GCC, have a problem when running on 32-bit machines, and `objdump` fails to generate .hex files. The bug affects both Windows and GNU/Linux machines. 64-bit builds are not affected. The bug is documented as [1810274](https://bugs.launchpad.net/gcc-arm-embedded/+bug/1810274).

The current solution is to upgrade to 8.2.1-1.2; the workaround is to
override `arm-none-eabi-objdump` with an older binary.

## Checksums

The SHA-256 hashes for the files are:

```txt
aa15729b8cd8e44a528e16b2119a6ad26c8dd55aa88c514570ecbb38bfcb0f9e ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.1-20190102-1122-centos32.tgz

1922394f8055d10d13288c233ae89a970c0e5f5ba307274e01c7d07ba916efe9 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.1-20190102-1122-centos64.tgz

9ca37228d8bf200505ffddd82111b8a444f9825720a14738dabb71bf3aa59c9f ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.1-20190102-1122-macos.tgz

610f1d659cdd9ec27afc881736fcc60dc37dbdc25585a00ce0118630dc9d550e ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.1-20190102-1122-win32.zip

c89031994b14840567a4c6cff31f10d5b51c2999a674fa75c8d09d1fe8c47d1b ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.1-20190102-1122-win64.zip
```
