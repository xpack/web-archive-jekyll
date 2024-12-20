---
title:  GNU MCU Eclipse ARM Embedded GCC v8.2.1-1.3 released
sidebar: arm-none-eabi-gcc

summary: "Version **8.2.1-1.3** is a maintenance release of **GNU MCU Eclipse ARM Embedded GCC** that fixes the GDB and liblto_plugin bugs present in the previous release."
app_name: "GNU MCU Eclipse ARM Embedded GCC"

download_url: https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/tag/v8.2.1-1.3/

date: 2019-02-02 12:35:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2019/02/02/arm-none-eabi-gcc-v8-2-1-1-3-released/

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
- the `-static` option was removed from the Windows build, to allow for
  the `liblto_plugin-0.dll` to be created; the `libwinpthread-1.dll` was
  copied to the `bin` folder
- the `liblto_plugin` copied/linked to the `lib/bdf-plugins` for `ar`
  to find it and be able to process archives with LTO objects.

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

### LTO & debugging on Windows

The Arm 8-2018-q4-major release introduced a problem on Windows, enabling
debugging information (`-g`/`-g3`) prevents `-flto` to properly link.
For Release configurations it is not a problem to remove the debug
options, but for Debug configurations this is unusable. The workaround
is to revert to the previous 7-2018-q2-update release, or to temporarily disable `-flto`. ([89183](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=89183))

### LTO & paths with spaces on Windows

When installing on Windows in locations with spaces in folder names,
the link step fails for builds using LTO.
([89249](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=89249))

## Checksums

The SHA-256 hashes for the files are:

```txt
b4dee573ac6ba0774da4d25a8478707c5ed49b64ebb20ef3ee057a2371b89e4b ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.3-20190202-1016-centos32.tgz

4893a8d1da0e0b656edc11fd3edee7abf13d65220c3b68b5ec0c579e71e86d9b ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.3-20190202-1016-centos64.tgz

ff5478b6b6d30b9ec5b4e1e4b57f2db08a74814b28a8e732bc2d5cb173093830 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.3-20190202-1016-macos.tgz

44a590d0b5856420d9cd51c4edd83b7d1d699971be99bb998bed773b2873501f ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.3-20190202-1016-win32.zip

b950137824629411abd8fec2f73f53a764a22c0688955f412b26595d7d961f70 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-8.2.1-1.3-20190202-1016-win64.zip
```
