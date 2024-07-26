---
title:  xPack CMake v3.18.3-1 released
sidebar: cmake

summary: "Version 3.18.3-1 is the first release of the **xPack CMake** package."

version: 3.18.3-1
npm_subversion: 1
download_url: https://github.com/xpack-dev-tools/cmake-xpack/releases/tag/v3.18.3-1/

date:   2020-09-29 14:20:00 +0300

comments: true

categories:
  - releases
  - cmake

tags:
  - releases
  - cmake
  - build

---

[The xPack CMake](https://xpack.github.io/dev-tools/cmake/)
is the **xPack** distribution of the
[CMake](https://cmake.org) build system.

There are separate binaries for **Windows** (Intel 32/64-bit),
**macOS** (Intel 64-bit) and **GNU/Linux** (Intel 32/64-bit, Arm 32/64-bit).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from GitHub [releases]({{ page.download_url }}).

## Install

The full details of installing the **xPack CMake** on various platforms
are presented in the separate
[Install]({{ site.baseurl }}/dev-tools/cmake/install/) page.

### Easy install

The easiest way to install CMake is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/cmake`](https://www.npmjs.com/package/@xpack-dev-tools/cmake)
from the [`npmjs.com`](https://www.npmjs.com) registry.

To install the latest version available, use:

```sh
xpm install --global @xpack-dev-tools/cmake@latest --verbose
```

To install this specific version, use:

```sh
xpm install --global @xpack-dev-tools/cmake@{{ page.version }}.{{ page.npm_subversion }}
```

## Compliance

The **xPack CMake** is based on the official
[CMake](https://cmake.org),
without any changes.

The current version is based on:

- CMake release
[3.18.3](https://github.com/Kitware/CMake/releases/tag/v3.18.3)
from Sep 22th, 2020.

## Changes

Compared to the upstream version, there are no functional changes.

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

### `@executable_path`

Similarly, on macOS, the binaries are adjusted with `otool` to use a
relative path.

## Documentation

The current version specific CMake documentation is available in each packet:

- `doc/cmake-X.Y/html/index.html`

and online from:

- [https://cmake.org/documentation/](https://cmake.org/documentation/)

## Supported platforms

Binaries for **Windows**, **macOS** and **GNU/Linux** are provided.

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
[README-MAINTAINER](https://github.com/xpack-dev-tools/cmake-xpack/blob/xpack/README-MAINTAINER.md) page.

## Travis tests

The first set of tests were performed on Travis, by running
a simple script to check if the binaries start on a wide range of
platforms and distributions:

- [test xPack CMake on stable platforms](https://travis-ci.org/github/xpack-dev-tools/cmake-xpack/builds/731239783)
- [test xPack CMake on latest platforms](https://travis-ci.org/github/xpack-dev-tools/cmake-xpack/builds/731243291)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
037bffd8c10769944e8754d637b8999ec4993c4666449e633969b4561c350321
xpack-cmake-3.18.3-1-darwin-x64.tar.gz

de64ad068f83134af8b3dc405a772f48c8b1ec518ffdb290701be56c8e284702
xpack-cmake-3.18.3-1-linux-arm64.tar.gz

1914f6df32081f6b2d3c1e51267a432cae2fb0a4d708640581006023b2af2ef9
xpack-cmake-3.18.3-1-linux-arm.tar.gz

0ee8c9e17dc366e354c846c910503916be668c18fae0da9c2a0a30e4fb6c3cab
xpack-cmake-3.18.3-1-linux-x32.tar.gz

8ef4f9dc5361ba73ee8a0d478c7f1c3de2c173c9ffd381e787fc16e6cbfdea07
xpack-cmake-3.18.3-1-linux-x64.tar.gz

4e0232170a4ed3682059317f3a3424eec7c8db98b883be90577fab632c67fda2
xpack-cmake-3.18.3-1-win32-x32.zip

ac6f880b501c00409b176ac29bcaa68c015fbd372b08edbc72e86e80a3812dea
xpack-cmake-3.18.3-1-win32-x64.zip
```

## Download analytics

- GitHub [xpack-dev-tools/cmake-xpack](https://github.com/xpack-dev-tools/cmake-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/cmake-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/cmake-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/cmake-xpack/total.svg)](https://github.com/xpack-dev-tools/cmake-xpack/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=cmake-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/cmake](https://www.npmjs.com/package/@xpack-dev-tools/cmake)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/cmake.svg)](https://www.npmjs.com/package/@xpack-dev-tools/cmake/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/cmake.svg)](https://www.npmjs.com/package/@xpack-dev-tools/cmake/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
