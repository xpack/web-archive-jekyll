---
title:  xPack GNU Arm Embedded GCC v11.3.1-1.1 released

summary: "Version **11.3.1-1.1** is a new release; it follows the Arm release."

arm_version: 11.3.Rel1
arm_date: August 8, 2022
version: 11.3.1-1.1
npm_subversion: 2
python_version: 10

download_url: https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/releases/tag/v11.3.1-1.1/

date: 2022-08-28 07:11:14 +0300

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
  - c++
  - exceptions

---

The [xPack GNU Arm Embedded GCC](https://xpack.github.io/dev-tools/arm-none-eabi-gcc/)
is a standalone cross-platform binary distribution of
[Arm GNU Toolchain](https://developer.arm.com/Tools%20and%20Software/GNU%20Toolchain).

There are separate binaries for **Windows** (Intel 64-bit),
**macOS** (Intel 64-bit, Apple Silicon 64-bit)
and **GNU/Linux** (Intel 64-bit, Arm 32/64-bit).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Prerequisites

- x64 GNU/Linux: any system with **GLIBC 2.27** or higher
  (like Ubuntu 18 or later, Debian 10 or later, RedHat 8 or later,
  Fedora 29 or later, etc)
- arm64/arm GNU/Linux: any system with **GLIBC 2.27** or higher
  (like Raspberry Pi OS, Ubuntu 18 or later, Debian 10 or later, RedHat 8 or later,
  Fedora 29 or later, etc)
- x64 Windows: Windows 7 with the Universal C Runtime
  ([UCRT](https://support.microsoft.com/en-us/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)),
  Windows 8, Windows 10
- x64 macOS: 10.13 or later
- arm64 macOS: 11.6 or later

## Install

The full details of installing the **xPack GNU Arm Embedded GCC** on various platforms
are presented in the separate [Install]({{ site.baseurl }}/dev-tools/arm-none-eabi-gcc/install/) page.

### Easy install

The easiest way to install Arm Embedded GCC is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/arm-none-eabi-gcc`](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc)
from the [`npmjs.com`](https://www.npmjs.com) registry.

With the `xpm` tool available, installing
the latest version of the package and adding it as
a dependency for a project is quite easy:

```sh
cd my-project
xpm init # Only at first use.

xpm install @xpack-dev-tools/arm-none-eabi-gcc@latest

ls -l xpacks/.bin
```

To install this specific version, use:

```sh
xpm install @xpack-dev-tools/arm-none-eabi-gcc@{{ page.version }}.{{ page.npm_subversion }}
```

For xPacks aware tools, like the **Eclipse Embedded C/C++ plug-ins**,
it is also possible to install Arm Embedded GCC globally, in the user home folder.

```sh
xpm install --global @xpack-dev-tools/arm-none-eabi-gcc@latest --verbose
```

Eclipse will automatically
identify binaries installed with
`xpm` and provide a convenient method to manage paths.

### Uninstall

To remove the links from the current project:

```sh
cd my-project

xpm uninstall @xpack-dev-tools/arm-none-eabi-gcc
```

To completely remove the package from the central xPacks store:

```sh
xpm uninstall --global @xpack-dev-tools/arm-none-eabi-gcc
```

## Compliance

The xPack GNU Arm Embedded GCC generally follows the official
[Arm Embedded GCC](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/downloads/) releases.

The current version is based on:

- [GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm)
release **{{ page.arm_version }}** from {{ page.arm_date }}
and uses the same sources. It includes:
  - GCC 11.3.1
  - binutils 2.38
  - newlib 4.1.0
  - GDB 12.1

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
thumb/v7-r+fp.sp/softfp;@mthumb@march=armv7-r+fp.sp@mfloat-abi=softfp
thumb/v7-r+fp.sp/hard;@mthumb@march=armv7-r+fp.sp@mfloat-abi=hard
thumb/v7-a/nofp;@mthumb@march=armv7-a@mfloat-abi=soft
thumb/v7-a+fp/softfp;@mthumb@march=armv7-a+fp@mfloat-abi=softfp
thumb/v7-a+fp/hard;@mthumb@march=armv7-a+fp@mfloat-abi=hard
thumb/v7-a+simd/softfp;@mthumb@march=armv7-a+simd@mfloat-abi=softfp
thumb/v7-a+simd/hard;@mthumb@march=armv7-a+simd@mfloat-abi=hard
thumb/v7ve+simd/softfp;@mthumb@march=armv7ve+simd@mfloat-abi=softfp
thumb/v7ve+simd/hard;@mthumb@march=armv7ve+simd@mfloat-abi=hard
thumb/v8-a/nofp;@mthumb@march=armv8-a@mfloat-abi=soft
thumb/v8-a+simd/softfp;@mthumb@march=armv8-a+simd@mfloat-abi=softfp
thumb/v8-a+simd/hard;@mthumb@march=armv8-a+simd@mfloat-abi=hard
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
thumb/v8.1-m.main+mve/hard;@mthumb@march=armv8.1-m.main+mve@mfloat-abi=hard
```

## Changes

Compared to the Arm version, there should be no functional changes.

### XML parsing in GDB

Some advanced GDB servers, like the one provided with SEGGER J-Link, are
capable of passing an XML with the target capabilities to the GDB client.
For unknown reasons, the Arm toolchain distribution came without XML
parsing support. The xPack distribution brings back support for
XML parsing and full integration with the SEGGER J-Link GDB server.

### Python

Support for Python scripting was added to GDB. This distribution provides
a separate binary, `arm-none-eabi-gdb-py3` with
support for **Python 3.{{ page.python_version }}**.

The Python 3 run-time is included, so GDB does not need any version of
Python to be installed, and is insensitive to the presence of other
versions.

Support for Python 2 was discontinued.

### Text User Interface (TUI)

Support for TUI was added to GDB. The `ncurses` library was added to
the distribution.

{% include note.html content="TUI is not available on Windows." %}

### No Guile

Due to the difficulties of building standalone Guile libraries on all
platforms, support for Guile scripting in GDB is currently not available.

## Bug fixes

- none

## Enhancements

- none

## Known problems

- none

## Shared libraries

On all platforms the packages are standalone, and expect only the standard
runtime to be present on the host.

All dependencies that are build as shared libraries are copied locally
in the `libexec` folder (or in the same folder as the executable for Windows).

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

### `@rpath` and `@loader_path`

Similarly, on macOS, the binaries are adjusted with `install_name_tool` to use a
relative path.

## Documentation

The original GNU GCC documentation is available
[online](https://gcc.gnu.org/onlinedocs/).

## Build

The binaries for all supported platforms
(Windows, macOS and GNU/Linux) were built using the
[xPack Build Box (XBB)](https://xpack.github.io/xbb/), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

The scripts used to build this distribution are in:

- `distro-info/scripts`

For the prerequisites and more details on the build procedure, please see the
[README-MAINTAINER](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/blob/xpack/README-MAINTAINER.md) page.

## CI tests

Before publishing, a set of simple tests were performed on an exhaustive
set of platforms. The results are available from:

- [GitHub Actions](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/actions/)
- [Travis CI](https://app.travis-ci.com/github/xpack-dev-tools/arm-none-eabi-gcc-xpack/builds/)

## Tests

The binaries were tested on a variety of platforms,
but mainly to check the integrity of the
build, not the compiler functionality.

## Checksums

The SHA-256 hashes for the files are:

```txt
99de78184f5548c65b980130c9438a31a602ddbbe9515f3d82bf000b67f8c835
xpack-arm-none-eabi-gcc-11.3.1-1.1-darwin-arm64.tar.gz

16dd4af277c488eae8a1f7bc8348f772fb0442946d767ea1ee77485ffe2ff848
xpack-arm-none-eabi-gcc-11.3.1-1.1-darwin-x64.tar.gz

2a7dcad87cc1b8498038a3e8263defa4fd61bc0e6179fe7a1eef0e09c79f30bd
xpack-arm-none-eabi-gcc-11.3.1-1.1-linux-arm.tar.gz

393baf6c478fd65ebb826b0f21a40f168d32600e16a2cb926c1fb288e8de3958
xpack-arm-none-eabi-gcc-11.3.1-1.1-linux-arm64.tar.gz

df515ea5b2efb625f1cf1e11c3d096c4ddf800408ee2bd061a67b7739a5febff
xpack-arm-none-eabi-gcc-11.3.1-1.1-linux-x64.tar.gz

d3906baa7a845bb8f341b67da8185e48fb9dc2746963bf40c2caea825c73ee5c
xpack-arm-none-eabi-gcc-11.3.1-1.1-win32-x64.zip

```

## Deprecation notices

### 32-bit support

Support for 32-bit Intel Linux and Intel Windows was
dropped in 2022. Support for 32-bit Arm Linux (armv7l) will be preserved
for a while, due to the large user base of 32-bit Raspberry Pi systems.

### Linux minimum requirements

Support for RedHat 7 was dropped in 2022 and the
minimum requirement was raised to GLIBC 2.27, available starting
with Ubuntu 18, Debian 10 and RedHat 8.

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
