---
title:  xPack CMake v3.18.6-1 released
sidebar: cmake

summary: "Version 3.18.6-1 is a new release of the **xPack CMake** package, following the CMake release."

version: 3.18.6-1
npm_subversion: 1
download_url: https://github.com/xpack-dev-tools/cmake-xpack/releases/tag/v3.18.6-1/

date:   2021-03-16 23:30:00 +0200

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

{% include note.html content="For consistency with the Node.js naming
conventions, the names of the Intel 32-bit images are now suffixed with
`-ia32`." %}

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
[3.18.6](https://github.com/Kitware/CMake/releases/tag/v3.18.6/)
from Feb 11th, 2021.

## Changes

Compared to the upstream version, the Windows version also supports
spawning scripts via `cmd.exe /c`. These scripts are used by **npm**/**xpm**
to redirect invocations to the global xPacks store.

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

- [test xPack CMake on stable platforms](https://travis-ci.com/github/xpack-dev-tools/cmake-xpack/builds/220317746)
- [test xPack CMake on latest platforms](https://travis-ci.com/github/xpack-dev-tools/cmake-xpack/builds/220317753)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
34e43ad10d740d816ddbf2025644ada1cd1de062ca862d7493d326e75e5e7ffb
xpack-cmake-3.18.6-1-darwin-x64.tar.gz

7d8dabbeb98d0e0ebda09163bd92b5ac395b129a7f7eb303cba2867f5d0bf39d
xpack-cmake-3.18.6-1-linux-arm64.tar.gz

8128a6ab83e31a8dd7e6877fb266a6a14dda139887e833bf2d11265652e87b39
xpack-cmake-3.18.6-1-linux-arm.tar.gz

74710d902c7d9f5a5c8ea751ac61c7f2a7c1ea25cd019af39be403487c965962
xpack-cmake-3.18.6-1-linux-ia32.tar.gz

61d4229a20748514da5604ed5c1ce28920139f701b563d3c5d001407b44c9663
xpack-cmake-3.18.6-1-linux-x64.tar.gz

eac1c5bb66acae7e13f7ed0daf94abc52f2870627814261213630d2fb28a236c
xpack-cmake-3.18.6-1-win32-ia32.zip

2d7793e5d89fee35ffe25798b842c2f78389fb85482f11f17dd4832efad05954
xpack-cmake-3.18.6-1-win32-x64.zip
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
