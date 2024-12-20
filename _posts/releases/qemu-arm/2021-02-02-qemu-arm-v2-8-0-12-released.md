---
title:  xPack QEMU Arm v2.8.0-12 released
sidebar: qemu-arm

summary: "Version **2.8.0-12** is a maintenance release; it fixes the macOS startup via links and enables Thumb2 for Arm v6."

version: 2.8.0-12
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/qemu-arm-xpack/releases/tag/v2.8.0-12/

date: 2021-02-02 11:30:00 +0200

redirect_to: https://xpack-dev-tools.github.io/qemu-arm-xpack/blog/2021/02/02/qemu-arm-v2-8-0-12-released/

comments: true

categories:
  - releases
  - qemu-arm

tags:
  - releases
  - qemu
  - emulator
  - arm
  - cortex-m

---

The [xPack QEMU Arm](https://xpack.github.io/dev-tools/qemu-arm/)
is the **xPack** distribution of the
[QEMU](https://www.qemu.org), with several extensions for Arm Cortex-M
devices.

There are separate binaries for **Windows** (x64 and x86),
**macOS** (x64) and **GNU/Linux** (x64 and x86, arm64 and arm).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Install

The full details of installing the **xPack QEMU Arm** on various platforms
are presented in the separate [Install]({{ site.baseurl }}/dev-tools/qemu-arm/install/) page.

### Easy install

The easiest way to install QEMU Arm is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/qemu-arm`](https://www.npmjs.com/package/@xpack-dev-tools/qemu-arm)
from the [`npmjs.com`](https://www.npmjs.com) registry.

To install the latest version available, use:

```sh
xpm install --global @xpack-dev-tools/qemu-arm@latest --verbose
```

To install this specific version, use:

```sh
xpm install --global @xpack-dev-tools/qemu-arm@{{ page.version }}.{{ page.npm_subversion }}
```

## Compliance

xPack QEMU Arm currently is based on the official [QEMU](https://www.qemu.org),
with major changes.

The current version is based on:

- QEMU version 2.8.0, commit [0737f32](https://github.com/xpack-dev-tools/qemu/commit/0737f32daf35f3730ed2461ddfaaf034c2ec7ff0) from Dec 20th, 2016.

## Changes

Compared to the master `qemu-system-arm`, the changes are major, all
application class Arm
devices were removed and replaced by several Cortex-M devices.

The supported boards are:

```console
xPack 64-bit QEMU v2.8.0 (qemu-system-gnuarmeclipse).

Supported boards:
  BluePill             BluePill STM32F103C8T6
  Maple                LeafLab Arduino-style STM32 microcontroller board (r5)
  NUCLEO-F072RB        ST Nucleo Development Board for STM32 F072 devices
  NUCLEO-F103RB        ST Nucleo Development Board for STM32 F1 series
  NUCLEO-F411RE        ST Nucleo Development Board for STM32 F4 series
  NetduinoGo           Netduino GoBus Development Board with STM32F4
  NetduinoPlus2        Netduino Development Board with STM32F4
  OLIMEXINO-STM32      Olimex Maple (Arduino-like) Development Board
  STM32-E407           Olimex Development Board for STM32F407ZGT6
  STM32-H103           Olimex Header Board for STM32F103RBT6
  STM32-P103           Olimex Prototype Board for STM32F103RBT6
  STM32-P107           Olimex Prototype Board for STM32F107VCT6
  STM32F0-Discovery    ST Discovery kit for STM32F051 line
  STM32F051-Discovery  ST Discovery kit for STM32F051 line
  STM32F4-Discovery    ST Discovery kit for STM32F407/417 lines
  STM32F429I-Discovery ST Discovery kit for STM32F429/439 lines
  generic              Generic Cortex-M board; use -mcu to define the device

Supported MCUs:
  STM32F051R8
  STM32F103RB
  STM32F107VC
  STM32F405RG
  STM32F407VG
  STM32F407VGTx <- new
  STM32F407ZG
  STM32F411RE
  STM32F429ZI
  STM32F429ZITx <- new>
```

Warning: support for hardware floating point on Cortex-M4 devices is not
available yet.

## Bug fixes

- [#14] - on macOS, starting the program via multiple symbolic links failed;
  fixed
- [#13] - on Cortex-M0, emulation of MSR/MRS instructions failed; support for
  Thumb2 instructions was enabled; similarly for barrier instructions

## Enhancements

- [#12] - add STM32F051-Discovery

## Known problems

- Ctrl-C does not interrupt the execution if the `--nographic` option is used.

## Shared libraries

On all platforms the packages are standalone, and expect only the standard
runtime (including X11) to be present on the host.

All dependencies that are build as shared libraries are copied locally in the
same folder as the executable.

### `DT_RPATH` and `LD_LIBRARY_PATH`

On GNU/Linux the binaries are adjusted to use a relative path:

```console
$ readelf -d library.so | grep rpath
 0x000000000000001d (RPATH)            Library runpath: [$ORIGIN]
```

In the GNU ld.so search strategy, the `DT_RPATH` has
the highest priority, higher than `LD_LIBRARY_PATH`, so if this later one
is set in the environment, it should not interfere with the xPack binaries.

Please note that previous versions, up to mid-2020, used `DT_RUNPATH`, which
has a priority lower than `LD_LIBRARY_PATH`, and does not tolerate setting
it in the environment.

### `@executable_path`

Similarly, on macOS, the binaries are adjusted with `otool` to use a
relative path.

## Documentation

The original documentation is available in the `share/doc` folder.

## Supported platforms

Binaries for **Windows**, **macOS** and **GNU/Linux** are provided.

The binaries were built using the
[xPack Build Box (XBB)](https://github.com/xpack/xpack-build-box), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

- x86/x64 GNU/Linux: all binaries were built with GCC 9.3, running in an
  Ubuntu 12 Docker container
- arm64/arm GNU/Linux: all binaries were built with GCC 9.3, running in an
  Ubuntu 16 Docker container (added in mid-2020)
- x86/x64 Windows: all binaries were built with mingw-w64 GCC 9.3, running in an
  Ubuntu 12 Docker container
- x64 macOS: all binaries were built with GCC 9.3, running in a separate
  folder on macOS 10.10.5.

## Build

The scripts used to build this distribution are in:

- `distro-info/scripts`

For the prerequisites and more details on the build procedure, please see the
[README-MAINTAINER](https://github.com/xpack-dev-tools/qemu-arm-xpack/blob/xpack/README-MAINTAINER.md) page.

## Travis tests

The first set of tests were performed on Travis, by running
a simple script to check if the binaries start on a wide range of
platforms and distributions:

- [test xPack QEMU Arm on stable platforms](https://travis-ci.org/github/xpack-dev-tools/qemu-arm-xpack/builds/757246668)
- [test xPack QEMU Arm on latest platforms](https://travis-ci.org/github/xpack-dev-tools/qemu-arm-xpack/builds/757246698)

## Tests

The binaries were testes on Windows 10 Pro 32/64-bit, Ubuntu 18 LTS 64-bit,
Xubuntu 18 LTS 32-bit and macOS 10.14.

The tests consist in running a simple blinky application
on the graphically emulated STM32F4DISCOVERY board. The binaries were
those generated by the
[simple Eclipse projects](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/tree/xpack/tests/eclipse)
available in the **xPack GNU Arm Embedded GCC** project. Use the
`arm-f4b-fs-debug-qemu` debug luncher available in the `arm-f4b-fs` project.

On platforms where Eclipse is not available, the binaries were
tested by manually starting the
blinky test on the emulated STM32F4DISCOVERY board.

```console
~/.local/xPacks/@xpack-dev-tools/qemu-arm/2.8.0-12.1/.content/bin/qemu-system-gnuarmeclipse --version

mkdir -p ~/Downloads
(cd ~/Downloads; curl -L --fail -o f407-disc-blink-tutorial.elf \
https://github.com/xpack-dev-tools/qemu-eclipse-test-projects/raw/master/f407-disc-blink-tutorial/Debug/f407-disc-blink-tutorial.elf)

~/.local/xPacks/@xpack-dev-tools/qemu-arm/2.8.0-12.1/.content/bin/qemu-system-gnuarmeclipse \
--board STM32F4-Discovery \
-d unimp,guest_errors \
--nographic \
--image ~/Downloads/f407-disc-blink-tutorial.elf \
--semihosting-config enable=on,target=native \
--semihosting-cmdline test 6

DISPLAY=:1.0 ~/opt/xPacks/@xpack-dev-tools/qemu-arm/2.8.0-12.1/.content/bin/qemu-system-gnuarmeclipse \
--board STM32F4-Discovery \
-d unimp,guest_errors \
--image ~/Downloads/f407-disc-blink-tutorial.elf \
--semihosting-config enable=on,target=native \
--semihosting-cmdline test 6
```

On Raspberry Pi OS 10 (buster) 64-bit the program was able to run in non
graphic mode, but did not start in graphic mode due to a
missing driver. To be further investigated.

## Checksums

The SHA-256 hashes for the files are:

```txt
1269339202b04fc765a7b1c37e0f46b0ecba5b880f26a43c7aa6a29f905e2edf
xpack-qemu-arm-2.8.0-12-darwin-x64.tar.gz

57c611d2469c227c71870a1ce5e0d35d88c0962795ea1a435a277db5f9fca79e
xpack-qemu-arm-2.8.0-12-linux-arm64.tar.gz

fa0a05ff7a31da9fb0228db4b7ee530e55d1bfe69bb1131a39f1d9a434bdcc91
xpack-qemu-arm-2.8.0-12-linux-arm.tar.gz

285553bb38785e8e070b610b4b701886e6456acc38b23d8b3a40563a72ee3513
xpack-qemu-arm-2.8.0-12-linux-ia32.tar.gz

834dd2e9ade20e23f8639cf42e6dc61940f350148e858bb1f22c2a43b398e280
xpack-qemu-arm-2.8.0-12-linux-x64.tar.gz

b78b3336ee75a561b70d0ba8f5da6fb34088cdc7cffd6a6e51a16c5d2fa1fcca
xpack-qemu-arm-2.8.0-12-win32-ia32.zip

9608c3aae54e379d3450955f3e9008f28dbbfe7add2f563c595f443bf270cc4d
xpack-qemu-arm-2.8.0-12-win32-x64.zip
```

## Download analytics

- GitHub [xpack-dev-tools/qemu-arm-xpack](https://github.com/xpack-dev-tools/qemu-arm-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/qemu-arm-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/qemu-arm-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/qemu-arm-xpack/total.svg)](https://github.com/xpack-dev-tools/qemu-arm-xpack/releases/)
  - all GNU MCU Eclipse releases [![Github All Releases](https://img.shields.io/github/downloads/gnu-mcu-eclipse/qemu/total.svg)](https://github.com/gnu-mcu-eclipse/qemu/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=qemu-arm-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/qemu-arm](https://www.npmjs.com/package/@xpack-dev-tools/qemu-arm)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/qemu-arm.svg)](https://www.npmjs.com/package/@xpack-dev-tools/qemu-arm/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/qemu-arm.svg)](https://www.npmjs.com/package/@xpack-dev-tools/qemu-arm/)
  - all @gnu-mcu-eclipse releases [![npm](https://img.shields.io/npm/dt/@gnu-mcu-eclipse/qemu.svg)](https://www.npmjs.com/package/@gnu-mcu-eclipse/qemu/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
