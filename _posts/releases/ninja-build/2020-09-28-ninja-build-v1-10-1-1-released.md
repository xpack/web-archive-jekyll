---
title:  xPack Ninja Build v1.10.1-1 released
sidebar: ninja-build

summary: "Version **1.10.1-1** is a new release of the **xPack Ninja Build** package."

version: 1.10.1-1
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/ninja-build-xpack/releases/tag/v1.10.1-1/

date: 2020-09-28 23:19:00 +0300

redirect_to: https://xpack-dev-tools.github.io/ninja-build-xpack/blog/2020/09/28/ninja-build-v1-10-1-1-released/

comments: true

categories:
  - releases
  - ninja-build

tags:
  - releases
  - ninja-build
  - ninja
  - build
  - speed
  - small

---

The [xPack Ninja Build](https://xpack.github.io/dev-tools/ninja-build/)
is the **xPack** distribution of the
[Ninja](https://ninja-build.org) build system.

There are separate binaries for **Windows** (x64 and x86),
**macOS** (x64) and **GNU/Linux** (x64 and x86, arm64 and arm).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Install

The full details of installing the **xPack Ninja Build** on various platforms
are presented in the separate [Install]({{ site.baseurl }}/dev-tools/ninja-build/install/) page.

### Easy install

The easiest way to install Ninja Build is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/ninja-build`](https://www.npmjs.com/package/@xpack-dev-tools/ninja-build)
from the [`npmjs.com`](https://www.npmjs.com) registry.

To install the latest version available, use:

```sh
xpm install --global @xpack-dev-tools/ninja-build@latest --verbose
```

To install this specific version, use:

```sh
xpm install --global @xpack-dev-tools/ninja-build@{{ page.version }}.{{ page.npm_subversion }}
```

## Compliance

The **xPack Ninja Build** is based on the official
[Ninja](https://ninja-build.org),
without any changes.

The current version is based on:

- Ninja release
[1.10.1](https://github.com/ninja-build/ninja/releases/tag/v1.10.1)
from Aug 18th, 2020.

## Bug fixes

- none

## Enhancements

- none

## Changes

Compared to the upstream version, there are no changes.

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

The original documentation is available from:

- [https://ninja-build.org/manual.html](https://ninja-build.org/manual.html)

## Supported platforms

Binaries for **Windows**, **macOS** and **GNU/Linux** are provided.

The binaries were built using the
[xPack Build Box (XBB)](https://github.com/xpack/xpack-build-box), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

- x86/x64 GNU/Linux: all binaries were built with GCC 9.3, running in an
  Ubuntu 12 Docker container
- arm64/arm GNU/Linux: all binaries were built with GCC 9.3, running in an
  Ubuntu 16 Docker container
- x86/x64 Windows: all binaries were built with mingw-w64 GCC 9.3, running in an
  Ubuntu 12 Docker container
- x64 macOS: all binaries were built with GCC 9.3, running in a separate
  folder on macOS 10.10.5.

## Build

The scripts used to build this distribution are in:

- `distro-info/scripts`

For the prerequisites and more details on the build procedure, please see the
[README-MAINTAINER](https://github.com/xpack-dev-tools/ninja-build-xpack/blob/xpack/README-MAINTAINER.md) page.

## Travis tests

The first set of tests were performed on Travis, by running
a simple script to check if the binaries start on a wide range of
platforms and distributions:

- [test xPack Ninja Build on stable platforms](https://travis-ci.org/github/xpack-dev-tools/ninja-build-xpack/builds/731081095)
- [test xPack Ninja Build on latest platforms](https://travis-ci.org/github/xpack-dev-tools/ninja-build-xpack/builds/731085775)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
7d75d2f20f8be2b61953fed26566b627517717831e700c22e0fbd23200a6ab45
xpack-ninja-build-1.10.1-1-darwin-x64.tar.gz

48ba6a6212c3d28eb08076f1946818a9067c523793b1db6c885904caa425dce4
xpack-ninja-build-1.10.1-1-linux-arm64.tar.gz

38df303e3f4c13ba58eaf5229fe0587eda9078a792f7063d7b60eec60f88b276
xpack-ninja-build-1.10.1-1-linux-arm.tar.gz

b170cf10ee12608d68d204f2ca8f77d423a0b095ee0d475db835c03829e08c38
xpack-ninja-build-1.10.1-1-linux-x32.tar.gz

7e8683b1e743cf7cae58f85ef500acea0f464a053ac3d4991383fdcefa550c29
xpack-ninja-build-1.10.1-1-linux-x64.tar.gz

6109815a8ed9b8423847fc368ea927b16b55bc3875135fbe642cf9ced0ed60d5
xpack-ninja-build-1.10.1-1-win32-x32.zip

160c3b3ec67d9f821871e947c8eb882ea5cf99e25a08ad03ebdfef2e04830e63
xpack-ninja-build-1.10.1-1-win32-x64.zip
```

## Download analytics

- GitHub [xpack-dev-tools/ninja-build-xpack](https://github.com/xpack-dev-tools/ninja-build-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/ninja-build-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/ninja-build-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/ninja-build-xpack/total.svg)](https://github.com/xpack-dev-tools/ninja-build-xpack/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=ninja-build-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/ninja-build](https://www.npmjs.com/package/@xpack-dev-tools/ninja-build)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/ninja-build.svg)](https://www.npmjs.com/package/@xpack-dev-tools/ninja-build/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/ninja-build.svg)](https://www.npmjs.com/package/@xpack-dev-tools/ninja-build/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
