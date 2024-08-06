---
title:  xPack Ninja Build v1.10.2-1 released
sidebar: ninja-build

summary: "Version 1.10.2-1 is a new release of the **xPack Ninja Build** package."

version: 1.10.2-1
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/ninja-build-xpack/releases/tag/v1.10.2-1/

date: 2020-12-19 12:14:00 +0200

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

[The xPack Ninja Build](https://xpack.github.io/dev-tools/ninja-build/)
is the **xPack** distribution of the
[Ninja](https://ninja-build.org) build system.

There are separate binaries for **Windows** (Intel 32/64-bit),
**macOS** (Intel 64-bit) and **GNU/Linux** (Intel 32/64-bit, Arm 32/64-bit).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

{% include note.html content="For consistency with the Node.js naming conventions, the names of the Intel 32-bit images are now suffixed with `-ia32`." %}

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
[1.10.2](https://github.com/ninja-build/ninja/releases/tag/v1.10.1)
from Nov 28th, 2020.

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

- Intel GNU/Linux: all binaries were built with GCC 9.3, running in an
  Ubuntu 12 Docker container
- Arm GNU/Linux: all binaries were built with GCC 9.3, running in an
  Ubuntu 16 Docker container
- Windows: all binaries were built with mingw-w64 GCC 9.3, running in an
  Ubuntu 12 Docker container
- macOS: all binaries were built with GCC 9.3, running in a separate
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

- [test xPack Ninja Build on stable platforms](https://travis-ci.org/github/xpack-dev-tools/ninja-build-xpack/builds/750535406)
- [test xPack Ninja Build on latest platforms](https://travis-ci.org/github/xpack-dev-tools/ninja-build-xpack/builds/750535435)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
06135291fd6153c6ea98243013e834dd3491c0e919b01dc22159f438006a18db
xpack-ninja-build-1.10.2-1-darwin-x64.tar.gz

df05a2ba777d7af2657325f9ff895252364d2a8c81083f1d7282974fae5a556a
xpack-ninja-build-1.10.2-1-linux-arm64.tar.gz

3af6ff22520383a5e0e539835a13114d5db055adfc899a1f61fb3b784f9141c3
xpack-ninja-build-1.10.2-1-linux-arm.tar.gz

2d72d42004033c6595e359e36634494aaad798bfacc2197827beb8007d73be52
xpack-ninja-build-1.10.2-1-linux-ia32.tar.gz

6c47cc86d549c1078d2d7c1ceb5f5b96c5c6768f6f1cb09866e95ca9dcee2b6e
xpack-ninja-build-1.10.2-1-linux-x64.tar.gz

cc8fc51d9394f8822ae88c4b479f2d5e15eae05ff87063c5e52f56c03e6adf5d
xpack-ninja-build-1.10.2-1-win32-ia32.zip

d9743f21206e0bd93729b05a1d909ab12f73e6facd2d016fc5fba2f62b0e57e2
xpack-ninja-build-1.10.2-1-win32-x64.zip
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
