---
title:  xPack Windows Build Tools v4.4.0-1 released

summary: "DEPRECATED: Version **4.4.0-1** is a new release of the **xPack Windows Build Tools** package, following the make release."

version: "4.4.0-1"
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/windows-build-tools-xpack/releases/tag/v4.4.0-1/

date: 2023-01-29 18:39:37 +0200

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

[The xPack Windows Build Tools](https://xpack.github.io/dev-tools/windows-build-tools/)
is a standalone Windows binary distribution of
**GNU make** and a few of other tools required by the Eclipse Embedded CDT
(formerly GNU MCU/ARM Eclipse) project, but the binaries can also be used in
generic build environments.

There are separate binaries for **Windows** (Intel 32/64-bit).

## Deprecated

Use v4.4.1-2.

## Download

The binary files are available from GitHub [Releases]({{ page.download_url }}).

## Prerequisites

- Intel Windows 64-bit: Windows 7 with the Universal C Runtime
  ([UCRT](https://support.microsoft.com/en-us/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)),
  Windows 8, Windows 10

## Install

The full details of installing the **xPack Windows Build Tools**
are presented in the separate
[Install]({{ site.baseurl }}/dev-tools/windows-build-tools/install/) page.

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

To remove the links created by xpm in the current project:

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

- [GNU make](https://ftpmirror.gnu.org/make/) version 4.4
- [Busybox](https://github.com/rmyorston/busybox-w32), the 5507c87
commit from Nov 9, 2022.

## Changes

There are no functional changes from original projects.

## Bug fixes

- the BusyBox code includes a patch around the UCRT bug that affects spawning
  sub-processes.

## Enhancements

- none

## Known problems

- starting with mid 2023, BusyBox included a make applet, which is preferred
  to GNU make; unfortunately it does not provides the full functionality
  and most builds fail; this applet was disabled in v4.4.1-2.

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
.../xpack-windows-build-tools-4.4.0-1/bin/make --version
```

A more elaborate test would be to run an Eclipse build.

## Checksums

The SHA-256 hashes for the files are:

```txt
f1209010daa21e040cc5bd455ea4736b28d965ab83f024d3e978c0853c192978
xpack-windows-build-tools-4.4.0-1-win32-x64.zip

```

## Deprecation notices

### 32-bit support

Support for 32-bit Intel Windows was dropped in 2022.

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
