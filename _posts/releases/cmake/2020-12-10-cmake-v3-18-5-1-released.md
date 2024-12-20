---
title:  xPack CMake v3.18.5-1 released
sidebar: cmake

summary: "Version **3.18.5-1** is a new release of the **xPack CMake** package, following the CMake release."

version: 3.18.5-1
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/cmake-xpack/releases/tag/v3.18.5-1/

date: 2020-12-10 21:33:00 +0200

redirect_to: https://xpack-dev-tools.github.io/cmake-xpack/blog/2020/12/10/cmake-v3-18-5-1-released/

comments: true

categories:
  - releases
  - cmake

tags:
  - releases
  - cmake
  - build

---

The [xPack CMake](https://xpack.github.io/dev-tools/cmake/)
is the **xPack** distribution of the
[CMake](https://cmake.org) build system.

There are separate binaries for **Windows** (x64 and x86),
**macOS** (x64) and **GNU/Linux** (x64 and x86, arm64 and arm).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Install

The full details of installing the **xPack CMake** on various platforms
are presented in the separate [Install]({{ site.baseurl }}/dev-tools/cmake/install/) page.

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
[3.18.5](https://github.com/Kitware/CMake/releases/tag/v3.18.5)
from Nov 18th, 2020.

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
[README-MAINTAINER](https://github.com/xpack-dev-tools/cmake-xpack/blob/xpack/README-MAINTAINER.md) page.

## Travis tests

The first set of tests were performed on Travis, by running
a simple script to check if the binaries start on a wide range of
platforms and distributions:

- [test xPack CMake on stable platforms](https://travis-ci.org/github/xpack-dev-tools/cmake-xpack/builds/748770562)
- [test xPack CMake on latest platforms](https://travis-ci.org/github/xpack-dev-tools/cmake-xpack/builds/748847225)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
ad0158cf6b953a87b4de518986c57bcc84026d2c5e20abb9f3a7b24c298ad4a6
xpack-cmake-3.18.5-1-darwin-x64.tar.gz

766433083ed06cdd58d6f609b8c935b3cc37631bf1e1678a140b3e6947f00537
xpack-cmake-3.18.5-1-linux-arm.tar.gz

8da9c7639922388f44dd4d945c2bb310625dd43de12eddcc59ada18298e87595
xpack-cmake-3.18.5-1-linux-arm64.tar.gz

0a1dc58070082817b96c902498b8ea8aa0bf7000819e24f96164c9f69be997f6
xpack-cmake-3.18.5-1-linux-ia32.tar.gz

209751cc6894b0450c6a8b516a940456632c1111610a94ff217b1f4e76206e4f
xpack-cmake-3.18.5-1-linux-x64.tar.gz

431ec2513730f1035df8da2e53ae5154494555c8c55c7464ae5be74ae5268a0f
xpack-cmake-3.18.5-1-win32-ia32.zip

b61236fc4e841899ff2f27608340fe31eb833574691de7674f2c2ac0a0abd2ba
xpack-cmake-3.18.5-1-win32-x64.zip
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
