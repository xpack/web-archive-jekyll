---
title:  xPack Meson Build v0.55.3-1 released
sidebar: meson-build

summary: "Version **0.55.3-1** is the first release of the **xPack Meson Build** package."

version: 0.55.3-1
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/meson-build-xpack/releases/tag/v0.55.3-1/

date: 2020-09-30 11:55:00 +0300

redirect_to: https://xpack-dev-tools.github.io/meson-build-xpack/blog/2020/09/30/meson-build-v0-55-3-1-released/

comments: true

categories:
  - releases
  - meson-build

tags:
  - releases
  - meson-build
  - meson
  - build
  - python
  - ninja

---

The [xPack Meson Build](https://xpack.github.io/dev-tools/meson-build/)
is the **xPack** distribution of the
[Meson](https://mesonbuild.com) build system.

There are separate binaries for **Windows** (x64 and x86),
**macOS** (x64) and **GNU/Linux** (x64 and x86, arm64 and arm).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Install

The full details of installing the **xPack Meson Build** on various platforms
are presented in the separate [Install]({{ site.baseurl }}/dev-tools/meson-build/install/) page.

### Easy install

The easiest way to install Meson Build is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/meson-build`](https://www.npmjs.com/package/@xpack-dev-tools/meson-build)
from the [`npmjs.com`](https://www.npmjs.com) registry.

To install the latest version available, use:

```sh
xpm install --global @xpack-dev-tools/meson-build@latest --verbose
```

To install this specific version, use:

```sh
xpm install --global @xpack-dev-tools/meson-build@{{ page.version }}.{{ page.npm_subversion }}
```

## Compliance

The **xPack Meson Build** is based on the official
[Meson](https://mesonbuild.com) build system,
without any changes.

The current version is based on:

- Meson release
[0.55.3](https://github.com/mesonbuild/meson/releases/tag/0.55.3)
from Sep 11th, 2020.

## Embedded Python

To simplify dependency management, this release embeds a Python
3.8.5 instance.

The `meson` executable is a standard ELF/EXE which includes the Python
run-time; the `main()` function prepares the Python environment and then
invokes the Meson main:

```python
  PyRun_SimpleString("from mesonbuild import mesonmain\n");
  PyRun_SimpleString("sys.exit(mesonmain.main())\n");
```

The Python library is located in the standard location:

- `lib/python3.8`
- `lib/python3.8/lib-dynload` (the platform dependent files)

The Meson files are located in:

- `lib/python3.8/mesonbuild`

To speed up execution, all Python files are compiled and are
available only as `.pyc`.

## Changes

- none

## Known problems

- [#1](https://github.com/xpack-dev-tools/meson-build-xpack/issues/1) - when
  installing meson as a project dependency, starting it fails on macOS, due
  to a bug preventing it to follow links; fixed in 0.55.3-2;
- [#2](https://github.com/xpack-dev-tools/meson-build-xpack/issues/2) - when
  generating commands in ninja.build that refer to itself, on GNU/Linux & macOS
  the path is not correct, it contains only a folder; fixed in 0.55.3-2.

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

- [https://mesonbuild.com/Manual.html](https://mesonbuild.com/Manual.html)

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
[README-MAINTAINER](https://github.com/xpack-dev-tools/meson-build-xpack/blob/xpack/README-MAINTAINER.md) page.

## Travis tests

The first set of tests were performed on Travis, by running
a simple script to check if the binaries start on a wide range of
platforms and distributions:

- [test xPack Meson Build on stable platforms](https://travis-ci.org/github/xpack-dev-tools/meson-build-xpack/builds/731542310)
- [test xPack Meson Build on latest platforms](https://travis-ci.org/github/xpack-dev-tools/meson-build-xpack/builds/731551368)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
f0b31f8ecbc90de4e8bff675d2e48527fefd5f44b17b34e9fd356fd1ab111e71
xpack-meson-build-0.55.3-1-darwin-x64.tar.gz

7f644d5762b75d48ac5bc865c31b29055ea9353fca4a49240493be32764b4714
xpack-meson-build-0.55.3-1-linux-arm64.tar.gz

8494dc993d38914dfd2d353c8fdc31c7420fb4511438cffeee9356f24239c922
xpack-meson-build-0.55.3-1-linux-arm.tar.gz

4762a7be6a7398b66a2c2dff80285a1e7e74d926896b9f0469bffa30b561b1d5
xpack-meson-build-0.55.3-1-linux-x32.tar.gz

83415e728359b7fba3fc9f9fb4ce0ea42c7681c99ff64f80598502055ae8d655
xpack-meson-build-0.55.3-1-linux-x64.tar.gz

16649ffa705c6906e2396c9f70f7f3aea493b283a635f0af5b613e1a226a65be
xpack-meson-build-0.55.3-1-win32-x32.zip

30d130de68238326d2b14712d460aab9bfac7413805d96303c15dc961b8fcf24
xpack-meson-build-0.55.3-1-win32-x64.zip
```

## Download analytics

- GitHub [xpack-dev-tools/meson-build-xpack](https://github.com/xpack-dev-tools/meson-build-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/meson-build-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/meson-build-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/meson-build-xpack/total.svg)](https://github.com/xpack-dev-tools/meson-build-xpack/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=meson-build-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/meson-build](https://www.npmjs.com/package/@xpack-dev-tools/meson-build)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/meson-build.svg)](https://www.npmjs.com/package/@xpack-dev-tools/meson-build/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/meson-build.svg)](https://www.npmjs.com/package/@xpack-dev-tools/meson-build/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
