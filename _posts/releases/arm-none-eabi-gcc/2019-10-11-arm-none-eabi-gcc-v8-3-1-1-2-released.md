---
title:  xPack GNU Arm Embedded GCC v8.3.1-1.2 released
sidebar: arm-none-eabi-gcc

summary: "Version **8.3.1-1.2** is  a maintenance release of xPack GNU Arm Embedded GCC to fix the **libgcov** build bug."

version: 8.3.1-1.2
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/releases/v8.3.1-1.2/

date: 2019-10-11 15:31:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2019/10/11/arm-none-eabi-gcc-v8-3-1-1-2-released/

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

## Install

The full details of installing the **xPack GNU Arm Embedded GCC** on
various platforms are presented in the separate [Install]({{ site.baseurl }}/dev-tools/arm-none-eabi-gcc/install/) page.

### Easy install

The easiest way to install GNU Arm Embedded GCC is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/arm-none-eabi-gcc`](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc)
from the [`npmjs.com`](https://www.npmjs.com) registry.

To install the latest version available, use:

```sh
xpm install --global @xpack-dev-tools/arm-none-eabi-gcc@latest --verbose
```

To install this specific version, use:

```sh
xpm install --global @xpack-dev-tools/arm-none-eabi-gcc@{{ page.version }}.{{ page.npm_subversion }}
```

## Compliance

This release follows the official
[GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm)
**8-2019-q3-update** release from July 10, 2019 and it is based on the
`gcc-arm-none-eabi-8-2019-q3-update-src.tar.bz2` source invariant.

For more details see the original Arm release text files:

- `distro-info/arm-readme.txt`
- `distro-info/arm-release.txt`

## Supported libraries

The supported libraries are:

```console
$ arm-none-eabi-gcc -print-multi-lib
.;
arm/v5te/softfp;@marm@march=armv5te+fp@mfloat-abi=softfp
arm/v5te/hard;@marm@march=armv5te+fp@mfloat-abi=hard
thumb/nofp;@mthumb@mfloat-abi=soft
thumb/v7/nofp;@mthumb@march=armv7@mfloat-abi=soft
thumb/v7+fp/softfp;@mthumb@march=armv7+fp@mfloat-abi=softfp
thumb/v7+fp/hard;@mthumb@march=armv7+fp@mfloat-abi=hard
thumb/v6-m/nofp;@mthumb@march=armv6s-m@mfloat-abi=soft
thumb/v7-m/nofp;@mthumb@march=armv7-m@mfloat-abi=soft
thumb/v7e-m/nofp;@mthumb@march=armv7e-m@mfloat-abi=soft
thumb/v7e-m+fp/softfp;@mthumb@march=armv7e-m+fp@mfloat-abi=softfp
thumb/v7e-m+fp/hard;@mthumb@march=armv7e-m+fp@mfloat-abi=hard
thumb/v7e-m+dp/softfp;@mthumb@march=armv7e-m+fp.dp@mfloat-abi=softfp
thumb/v7e-m+dp/hard;@mthumb@march=armv7e-m+fp.dp@mfloat-abi=hard
thumb/v8-m.base/nofp;@mthumb@march=armv8-m.base@mfloat-abi=soft
thumb/v8-m.main/nofp;@mthumb@march=armv8-m.main@mfloat-abi=soft
thumb/v8-m.main+fp/softfp;@mthumb@march=armv8-m.main+fp@mfloat-abi=softfp
thumb/v8-m.main+fp/hard;@mthumb@march=armv8-m.main+fp@mfloat-abi=hard
thumb/v8-m.main+dp/softfp;@mthumb@march=armv8-m.main+fp.dp@mfloat-abi=softfp
thumb/v8-m.main+dp/hard;@mthumb@march=armv8-m.main+fp.dp@mfloat-abi=hard
```

## Changes

There should be no functional changes.

### `libgcov`

[[#1]](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/issues/1)
Due to an omission in the build scripts, the content of the `libgcov`
library was mostly empty; the script was fixed and now the library has the
expected content.

### `lib/bdf-plugins`

To improve LTO support, the `lib/bdf-plugins` folder was added, with
a link to the `liblto_plugin.so` library (a file copy on Windows).

This allows the use of traditional program names, like `arm-none-eabi-ar`
instead of the new `arm-none-eabi-gcc-ar`, without getting errors like:

```sh
arm-none-eabi-ar -r  "libarm-static-lib.a"  ./lib.o
arm-none-eabi-ar: creating libarm-static-lib.a
arm-none-eabi-ar: ./lib.o: plugin needed to handle lto object <---
```

The issue was reported to Arm as bug [1838049](https://bugs.launchpad.net/gcc-arm-embedded/+bug/1838049).

### Python 3

Partial experimental support for Python 3 was added to GDB for GNU/Linux
and macOS; not yet available on Windows
([24469](https://sourceware.org/bugzilla/show_bug.cgi?id=24469)).

## Known problems

- none

## Documentation

The original PDF documentation is available in the `share/doc` folder.

## Supported platforms

Binaries for **Windows**, **macOS** and **GNU/Linux** are provided.

The binaries were built using the
[xPack Build Box (XBB)](https://github.com/xpack/xpack-build-box), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

- x86/x64 GNU/Linux: all binaries were built with GCC 7.4, running in a CentOS 6
  Docker container
- x86/x64 Windows: all binaries were built with mingw-w64 GCC 7.4, running in a
  CentOS 6 Docker container
- x64 macOS: most binaries were built with GCC 7.4, running in a separate
  folder on macOS 10.10.5; GDB cannot be compiled with GCC, so Apple
  clang was used.

## Tests

The binaries were testes on Windows 10 Pro 32/64-bit, Ubuntu 18 LTS 64-bit,
Xubuntu 18 LTS 32-bit and macOS 10.13.

The tests consist in building and debugging some
[simple Eclipse projects](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/tree/xpack/tests/eclipse)
available in the project.

Since the source code used for GCC is identical to the one used by Arm, the
long and complex tests performed by Arm to validate their release were not
executed again.

## Checksums

The SHA-256 hashes for the files are:

```txt
f0192ac5ec9bb5ac0c2e8590c110b0265e81ee92f8912961827cccc693827d13
xpack-arm-none-eabi-gcc-8.3.1-1.2-darwin-x64.tgz

d49ed1e2eb40c0ec73c7ea3f38216da0445d420bdfd25fef2bffaed3fe75d845
xpack-arm-none-eabi-gcc-8.3.1-1.2-linux-x32.tgz

a5e76ad1b89a1cf0ef5be5be5e8de862452f388e041d59dede237c5b27a15c5b
xpack-arm-none-eabi-gcc-8.3.1-1.2-linux-x64.tgz

d6eab345b254b331036856416da1591f4f8bd633a2718b72d93324468240aadf
xpack-arm-none-eabi-gcc-8.3.1-1.2-win32-x32.zip

5d89caf249c7f048b6549bf1a6f88d2736aacfa5e23eaa16a03fd32ab87ffbdf
xpack-arm-none-eabi-gcc-8.3.1-1.2-win32-x64.zip
```

## Download analytics

- GitHub [xpack-dev-tools/arm-none-eabi-gcc-xpack](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/arm-none-eabi-gcc-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/arm-none-eabi-gcc-xpack/total.svg)](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/releases/)
  - all GNU MCU Eclipse releases [![Github All Releases](https://img.shields.io/github/downloads/gnu-mcu-eclipse/arm-none-eabi-gcc/total.svg)](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=arm-none-eabi-gcc-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/arm-none-eabi-gcc](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/arm-none-eabi-gcc.svg)](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/arm-none-eabi-gcc.svg)](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc/)
  - all @gnu-mcu-eclipse releases [![npm](https://img.shields.io/npm/dt/@gnu-mcu-eclipse/arm-none-eabi-gcc.svg)](https://www.npmjs.com/package/@gnu-mcu-eclipse/arm-none-eabi-gcc/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
