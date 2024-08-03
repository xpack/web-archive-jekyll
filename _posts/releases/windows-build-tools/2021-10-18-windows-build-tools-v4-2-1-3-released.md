---
title:  xPack Windows Build Tools v4.2.1-3 released
sidebar: windows-build-tools

summary: "DO NOT USE! Version **4.2.1-3** is a maintenance release; it updates to the latest upstream Busybox and to the new build scripts."

version: 4.2.1-3
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/windows-build-tools-xpack/releases/tag/v4.2.1-3/

date: 2021-10-18 16:48:31 +0300

comments: true

categories:
  - releases
  - windows-build-tools

tags:
  - releases
  - windows-build-tools
  - build
  - make
  - rm
  - mkdir
  - busybox

---

{% include warning.html content="This version is affected by the Windows UCRT bug, `make` throws _Error -1073741819_; please use v4.3.x or later. Thank you for your understanding." %}

[The xPack Windows Build Tools](https://xpack.github.io/dev-tools/windows-build-tools/)
is a standalone Windows binary distribution of
**GNU make** and a few of other tools required by the Eclipse Embedded CDT
(formerly GNU MCU/ARM Eclipse) project, but the binaries can also be used in
generic build environments.

There are separate binaries for **Windows** (Intel 32/64-bit).

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Prerequisites

- Intel Windows 32/64-bit: Windows 7 with the Universal C Runtime
  ([UCRT](https://support.microsoft.com/en-us/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)),
  Windows 8, Windows 10

## Install

The full details of installing the **xPack Windows Build Tools**
are presented in the separate [Install]({{ site.baseurl }}/dev-tools/windows-build-tools/install/) page.

### Easy install

The easiest way to install Windows Build Tools is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/windows-build-tools`](https://www.npmjs.com/package/@xpack-dev-tools/windows-build-tools)
from the [`npmjs.com`](https://www.npmjs.com) registry.

With the `xpm` tool available, installing
the latest version of the package and adding it as
a dependency for a project is quite easy:

```sh
cd my-project
xpm init # Only at first use.

xpm install @xpack-dev-tools/windows-build-tools@latest

ls -l xpacks/.bin
```

To install this specific version, use:

```sh
xpm install @xpack-dev-tools/windows-build-tools@{{ page.version }}.{{ page.npm_subversion }}
```

For xPacks aware tools, like the **Eclipse Embedded C/C++ plug-ins**,
it is also possible to install Windows Build Tools globally, in the user home folder.

```sh
xpm install --global @xpack-dev-tools/windows-build-tools@latest --verbose
```

Eclipse will automatically
identify binaries installed with
`xpm` and provide a convenient method to manage paths.

### Uninstall

To remove the links from the current project:

```sh
cd my-project

xpm uninstall @xpack-dev-tools/windows-build-tools
```

To completely remove the package from the central xPacks store:

```sh
xpm uninstall --global @xpack-dev-tools/windows-build-tools
```

## Compliance

The xPack Windows Build Tools uses programs from other projects.

The current version is based on:

- [GNU make](https://ftpmirror.gnu.org/make/) version 4.2.1
- [Busybox](https://github.com/rmyorston/busybox-w32), the d239d2d5
commit from Oct 17, 2021.

## Changes

There are no functional changes from original projects.

## Bug fixes

- none

## Enhancements

- none

## Known problems

- [#19](https://github.com/xpack-dev-tools/windows-build-tools-xpack/issues/19)
  A bug was identified in [Microsoft UCRT](https://github.com/xpack-dev-tools/ms-spawn-issue),
  affecting programs which spawn subprocesses, like `sh.exe`, `make.exe`, etc;
  a workaround was identified for BusyBox, and the problem was fixed in
  v4.3.0-1.

## Shared libraries

The dependencies are either linked as static libraries or the
DLLs are included, so the binaries should run on any Windows system.

## Documentation

- none

## Build

The binaries were built using the
[xPack Build Box (XBB)](https://xpack.github.io/xbb/), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

The scripts used to build this distribution are in:

- `distro-info/scripts`

For the prerequisites and more details on the build procedure, please see the
[README-MAINTAINER](https://github.com/xpack-dev-tools/windows-build-tools-xpack/blob/xpack/README-MAINTAINER.md) page.

## CI tests

Before publishing, a set of simple tests were performed on an exhaustive
set of platforms. The results are available from:

- [GitHub Actions](https://github.com/xpack-dev-tools/windows-build-tools-xpack/actions/)

## Tests

The binaries were testes on Windows 10 Pro 32/64-bit.

Install the package with xpm.

The simple test, consists in starting the binary.

```sh
.../xpack-windows-build-tools-4.2.1-3/bin/make --version
```

A more elaborate test would be to run an Eclipse build.

## Checksums

The SHA-256 hashes for the files are:

```txt
939edfd488642693fadf564e5285cbb388bad2bd550b6b061a4b54daf58eca47
xpack-windows-build-tools-4.2.1-3-win32-ia32.zip

f3081840c0bb7df1abc4d3379546ea7286b2f0282cc148ed105a23432bbc6f9b
xpack-windows-build-tools-4.2.1-3-win32-x64.zip

```

## Deprecation notices

### 32-bit support

Support for 32-bit Intel Linux and Intel Windows will most probably
be dropped in 2022. Support for 32-bit Arm Linux will be preserved
for a while, due to the large user base of 32-bit Raspberry Pi systems.

### Linux minimum requirements

Support for RedHat 7 will most probably be dropped in 2022, and the
minimum requirement will be raised to GLIBC 2.27, available starting
with Ubuntu 18 and RedHat 8.

## Download analytics

- GitHub [xpack-dev-tools/windows-build-tools-xpack.git](https://github.com/xpack-dev-tools/windows-build-tools-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/windows-build-tools-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/windows-build-tools-xpack/releases/v{{ page.version }}/)
  - all releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/windows-build-tools-xpack/total.svg)](https://github.com/xpack-dev-tools/windows-build-tools-xpack/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=windows-build-tools-xpack) (grouped per release)
- xPack [@xpack-dev-tools/windows-build-tools](https://github.com/xpack-dev-tools/windows-build-tools-xpack/)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/windows-build-tools.svg)](https://www.npmjs.com/package/@xpack-dev-tools/windows-build-tools/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/windows-build-tools.svg)](https://www.npmjs.com/package/@xpack-dev-tools/windows-build-tools/)
  - all @gnu-mcu-eclipse releases [![npm](https://img.shields.io/npm/dt/@gnu-mcu-eclipse/windows-build-tools.svg)](https://www.npmjs.com/package/@gnu-mcu-eclipse/windows-build-tools/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
