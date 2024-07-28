---
title:  xPack OpenOCD v0.10.0-15 released
sidebar: openocd

summary: "Version 0.10.0-15 is a maintenance release; it updates to the latest upstream master."

version: 0.10.0-15
npm_subversion: 3

download_url: https://github.com/xpack-dev-tools/openocd-xpack/releases/tag/v0.10.0-15/

date: 2020-10-13 21:33:00 +0300

comments: true

categories:
  - releases
  - openocd

tags:
  - releases
  - openocd

---

[The xPack OpenOCD](https://xpack.github.io/dev-tools/openocd/)
is the **xPack** distribution of
[OpenOCD](https://openocd.org).

There are separate binaries for **Windows** (Intel 32/64-bit),
**macOS** (Intel 64-bit) and **GNU/Linux** (Intel 32/64-bit, Arm 32/64-bit).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from GitHub [releases]({{ page.download_url }}).

## Install

The full details of installing the **xPack OpenOCD** on various platforms
are presented in the separate
[Install]({{ site.baseurl }}/dev-tools/openocd/install/) page.

### Easy install

The easiest way to install OpenOCD is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/openocd`](https://www.npmjs.com/package/@xpack-dev-tools/openocd)
from the [`npmjs.com`](https://www.npmjs.com) registry.

To install the latest version available, use:

```sh
xpm install --global @xpack-dev-tools/openocd@latest --verbose
```

To install this specific version, use:

```sh
xpm install --global @xpack-dev-tools/openocd@{{ page.version }}.{{ page.npm_subversion }}
```

## Compliance

The **xPack OpenOCD** generally follows the official
[OpenOCD](https://openocd.org) releases.

The current version is based on:

- OpenOCD version 0.10.0, the development commit
[3ffa14b04](https://github.com/xpack-dev-tools/openocd/commit/3ffa14b043225b9766132b1979db7ddb8d91ba5e)
from October 11, 2020.

## Changes

There are no functional changes.

Compared to the upstream, the following changes were applied:

- a configure option was added to configure branding (`--enable-branding`)
- the `src/openocd.c` file was edited to display the branding string
- the `contrib/60-openocd.rules` file was simplified to avoid protection
  related issues.

## Bug fixes

- none

## Enhancements

- none

## Known problems

- none

## Shared libraries

On all platforms the packages are standalone, and expect only the standard
runtime to be present on the host.

All dependencies that are build as shared libraries are copied locally in the
same folder as the executable.

### `DT_RPATH` and `LD_LIBRARY_PATH`

On GNU/Linux the binaries are adjusted to use a relative path:

```console
$ readelf -d library.so | grep runpath
 0x000000000000001d (RPATH)            Library rpath: [$ORIGIN]
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

Binaries for **Windows**, **macOS** and **Intel/Arm GNU/Linux** are provided.

The binaries were built using the
[xPack Build Box (XBB)](https://github.com/xpack/xpack-build-box), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

- Intel GNU/Linux: all binaries were built with GCC 9.3, running in an
  Ubuntu 12 Docker container
- Arm GNU/Linux: all binaries were built with GCC 9.3, running in an
  Ubuntu 16 Docker container (added in mid-2020)
- Windows: all binaries were built with mingw-w64 GCC 9.3, running in an
  Ubuntu 12 Docker container
- macOS: all binaries were built with GCC 9.3, running in a separate
  folder on macOS 10.10.5.

## Build

The scripts used to build this distribution are in:

- `distro-info/scripts`

For the prerequisites and more details on the build procedure, please see the
[README-MAINTAINER](https://github.com/xpack-dev-tools/openocd-xpack/blob/xpack/README-MAINTAINER.md) page.

## Travis tests

The first set of tests were performed on Travis, by running
a simple script to check if the binaries start on a wide range of
platforms and distributions:

- [test xPack OpenOCD on stable platforms](https://travis-ci.org/github/xpack-dev-tools/openocd-xpack/builds/735490849)
- [test xPack OpenOCD on latest platforms](https://travis-ci.org/github/xpack-dev-tools/openocd-xpack/builds/735491108)

## Tests

The binaries were testes on Windows 11 Pro, Intel Ubuntu 22
LTS and macOS 14.5.

Install the package with xpm.

The simple test, consists in starting the binaries
only to identify the STM32F4DISCOVERY board.

```sh
~/Library/xPacks/@xpack-dev-tools/openocd/{{ page.version }}.{{ page.npm_subversion }}/.content/bin/openocd -f board/stm32f4discovery.cfg
```

A more complex test consist in programming and debugging a simple blinky
application on the STM32F4DISCOVERY board. The binaries were
those generated by
[simple Eclipse projects](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/tree/xpack/tests/eclipse)
available in the **xPack GNU Arm Embedded GCC** project.

## Checksums

The SHA-256 hashes for the files are:

```txt
370915b252ff3096b46663943fa040296d75991431228c5cfe315082cff10cab
xpack-openocd-0.10.0-15-darwin-x64.tar.gz

874c0bb93812109f4136b8b4670702ae4d76aa0d6327989a30596cabf4e052b5
xpack-openocd-0.10.0-15-linux-arm64.tar.gz

7697144b4f6581aa0b16e02b8c07f4b91ad861088263327c21fa340b1854ca06
xpack-openocd-0.10.0-15-linux-arm.tar.gz

68f02f2b392c2036702a7da9f418203b60f24aea30b59154e9e5042c1dc567dc
xpack-openocd-0.10.0-15-linux-x32.tar.gz

0a880ef296da083c4eb06ed589181414ae73d64a7dcec5642676207aeacc3e54
xpack-openocd-0.10.0-15-linux-x64.tar.gz

34f05809057ca851ac9c7f8925095abbf9b0c3594a7ca904e4bed3a7f2edfbc8
xpack-openocd-0.10.0-15-win32-x32.zip

6bd6999f7371f68ccc861cf84133feef9976e91fc6a29ef2740d6bd3e4ff203f
xpack-openocd-0.10.0-15-win32-x64.zip
```

## Download analytics

- GitHub [xpack-dev-tools/openocd-xpack](https://github.com/xpack-dev-tools/openocd-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/openocd-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/openocd-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/openocd-xpack/total.svg)](https://github.com/xpack-dev-tools/openocd-xpack/releases/)
  - all GNU MCU Eclipse releases [![Github All Releases](https://img.shields.io/github/downloads/gnu-mcu-eclipse/openocd/total.svg)](https://github.com/gnu-mcu-eclipse/openocd/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=openocd-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/openocd](https://www.npmjs.com/package/@xpack-dev-tools/openocd)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/openocd.svg)](https://www.npmjs.com/package/@xpack-dev-tools/openocd/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/openocd.svg)](https://www.npmjs.com/package/@xpack-dev-tools/openocd/)
  - all @gnu-mcu-eclipse releases [![npm](https://img.shields.io/npm/dt/@gnu-mcu-eclipse/openocd.svg)](https://www.npmjs.com/package/@gnu-mcu-eclipse/openocd/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
