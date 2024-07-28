---
title:  xPack CMake v3.19.8-1 released
sidebar: cmake

summary: "Version 3.19.8-1 is a new release of the **xPack CMake** package, following the CMake release."

version: 3.19.8-1
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/cmake-xpack/releases/tag/v3.19.8-1/

date: 2021-05-19 15:28:00 +0300

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
[CMake](https://cmake.org).

The current version is based on:

- CMake release
[3.19.8](https://github.com/Kitware/CMake/releases/tag/v3.19.8/)
from Apr 6th, 2021.

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

- [test xPack CMake on stable platforms](https://travis-ci.com/github/xpack-dev-tools/cmake-xpack/builds/226305413)
- [test xPack CMake on latest platforms](https://travis-ci.com/github/xpack-dev-tools/cmake-xpack/builds/226305446)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
192179afc42b1a5fed15639a81ea827759ed839d7cdb70954813a5f383800a02
xpack-cmake-3.19.8-1-darwin-x64.tar.gz

c18f5a8c5b0fd913fd8ff5f9429e95fcf684d4b919cbab092ca73ef214caf539
xpack-cmake-3.19.8-1-linux-arm64.tar.gz

b218ae4333d9c79b91b1b61094b81622c09df2257e5e58a2903318278716cdd6
xpack-cmake-3.19.8-1-linux-arm.tar.gz

a318e5e68347c18f3fd9f029fd28e2797db668580c8877b116036149f2975769
xpack-cmake-3.19.8-1-linux-ia32.tar.gz

b83fe5b748a2b10a82c1496409cdbedb8a50648bb430cfba79cb01ec1b8cf043
xpack-cmake-3.19.8-1-linux-x64.tar.gz

3cea05c876fcda189e4d81f58a5effaa156e79254253bbcd889df3e8e00f5842
xpack-cmake-3.19.8-1-win32-ia32.zip

7d8bf87ce93420dc054612199c0865b27ca91a264264f12b0851efda8bca9678
xpack-cmake-3.19.8-1-win32-x64.zip
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
