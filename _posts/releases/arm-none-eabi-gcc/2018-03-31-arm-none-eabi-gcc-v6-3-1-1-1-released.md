---
title:  GNU MCU Eclipse ARM Embedded GCC v6.3.1-1.1 released
sidebar: arm-none-eabi-gcc

summary: "Version **6.3.1-1.1** is the first release of **GNU MCU Eclipse ARM Embedded GCC**."
app_name: "GNU MCU Eclipse ARM Embedded GCC"

download_url: https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/tag/v6.3.1-1.1/

date: 2018-03-31 12:00:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2018/03/31/arm-none-eabi-gcc-v6-3-1-1-1-released/

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

This release follows the official [GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm)  **6-2017-q2-update** release from June 28, 2017 and it is based on the `gcc-arm-none-eabi-6-2017-q2-update-src.tar.bz2` source invariant.

## Binaries

Binaries for **Windows**, **macOS** and **GNU/Linux** are provided.

The GNU/Linux binaries were built on two CentOS 6 Docker images (32/64-bit), and run on any distribution based on CentOS 6 or later.

The macOS binary was built on a macOS 10.10.5 and must run on any newer macOS system.

The Windows binaries were built with mingw-w64, and run on any reasonably recent **i686** and **x86_64** Windows machines.

Instructions on how to install the binaries are available in the separate [How to install the ARM toolchain?]({{ site.baseurl }}/dev-tools/arm-none-eabi-gcc/install/) page.

The toolchain is also available as an [xPack](https://www.npmjs.com/package/@gnu-mcu-eclipse/arm-none-eabi-gcc) and can be conveniently installed with [`xpm`](https://www.npmjs.com/package/xpm):

```sh
xpm install --global @gnu-mcu-eclipse/arm-none-eabi-gcc@latest
```

This installs the latest available version.

For better control and repeatability, the build scripts use Docker containers; all files required during builds are available as a separate [gnu-mcu-eclipse/arm-none-eabi-gcc-build](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc-build) project.

## Known problems

* none

## Checksums

The SHA-256 hashes for the files are:

```txt
f4262eb3bd6c9b67894384ea6a3778a7d606be5d5d1f3c635c3ffe57c60fbda5 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-6.3.1-1.1-20180331-0618-centos32.tgz

b7f08ebedec5a2da9ba59a8a6eadf65217e9998478a35ebe634713d4236bf972 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-6.3.1-1.1-20180331-0618-centos64.tgz

80ad64fa60915b591ff02c58522c0ff9d64a2abf1ab3e3850ed9556a653c4686 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-6.3.1-1.1-20180331-0618-osx.tgz

ad23df4fde3cc0153e910e459e5fada5b9b1d4a73d9651b96e21d0be73f8a7e6 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-6.3.1-1.1-20180331-0618-win32.zip

37cdad0da139808f62146be9f1860a87883c8a5ec1afb6822db4e7c8dba25f35 ?
gnu-mcu-eclipse-arm-none-eabi-gcc-6.3.1-1.1-20180331-0618-win64.zip
```
