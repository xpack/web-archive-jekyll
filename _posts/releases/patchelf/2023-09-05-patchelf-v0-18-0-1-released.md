---
title:  xPack NixOS PatchELF v0.18.0-1 released

summary: "Version **0.18.0-1** is a new release; it follows the upstream release."

patchelf_version: "0.18.0"
patchelf_date: "23 Apr 2023"

version: "0.18.0-1"
npm_subversion: "1"

download_url: https://github.com/xpack-dev-tools/patchelf-xpack/releases/tag/v0.18.0-1/

comments: true

date:   2023-09-05 21:27:29 +0300

# For Jekyll releases selection.
categories:
  - releases
  - patchelf

# For navigation; use scripts/createtag.sh in Jekyll.
tags:
  - releases
  - patchelf

---

[The xPack NixOS PatchELF](https://xpack.github.io/patchelf/)
is a standalone cross-platform binary distribution of
[NixOS PatchELF](https://github.com/NixOS/patchelf/).

There are separate binaries for
**macOS** (Intel 64-bit, Apple Silicon 64-bit)
and **GNU/Linux** (Intel 64-bit, Arm 32/64-bit).

{% include note.html content="The main targets for the Arm binaries
are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from GitHub [Releases]({{ page.download_url }}).

## Prerequisites

- GNU/Linux Intel 64-bit: any system with **GLIBC 2.27** or higher
  (like Ubuntu 18 or later, Debian 10 or later, RedHat 8 later,
  Fedora 29 or later, etc)
- GNU/Linux Arm 32/64-bit: any system with **GLIBC 2.27** or higher
  (like Raspberry Pi OS, Ubuntu 18 or later, Debian 10 or later, RedHat 8 later,
  Fedora 29 or later, etc)
- Intel macOS 64-bit: 10.13 or later
- Apple Silicon macOS 64-bit: 11.6 or later

## Install

The full details of installing the **xPack NixOS PatchELF** on various platforms
are presented in the separate
[Install]({{ site.baseurl }}/dev-tools/patchelf/install/) page.

### Easy install

The easiest way to install NixOS PatchELF is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/patchelf`](https://www.npmjs.com/package/@xpack-dev-tools/patchelf)
from the [`npmjs.com`](https://www.npmjs.com) registry.

With the `xpm` tool available, installing
the latest version of the package and adding it as
a development dependency for a project is quite easy:

```sh
cd my-project
xpm init # Add a package.json if not already present

xpm install @xpack-dev-tools/patchelf@latest --verbose

ls -l xpacks/.bin
```

To install this specific version, use:

```sh
xpm install @xpack-dev-tools/patchelf@{{ page.version }}.{{ page.npm_subversion }} --verbose
```

It is also possible to install Meson Build globally, in the user home folder,
but this requires xPack aware tools to automatically identify them and
manage paths.

```sh
xpm install --global @xpack-dev-tools/patchelf@latest --verbose
```

### Uninstall

To remove the links created by xpm in the current project:

```sh
cd my-project

xpm uninstall @xpack-dev-tools/patchelf
```

To completely remove the package from the central xPack store:

```sh
xpm uninstall --global @xpack-dev-tools/patchelf
```

## Compliance

The xPack NixOS PatchELF generally follows the official
[NixOS PatchELF](https://github.com/NixOS/patchelf) releases.

The current version is based on:

- NixOS PatchELF version {{ page.patchelf_version }}
from {{ page.patchelf_date }}.

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

The original documentation is available
[online](https://github.com/NixOS/patchelf/).

## Build

The binaries for all supported platforms
(Windows, macOS and GNU/Linux) were built using the
[xPack Build Box (XBB)](https://xpack.github.io/xbb/), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

For the prerequisites and more details on the build procedure, please see the
[How to build](https://github.com/xpack-dev-tools/patchelf-xpack/blob/xpack/README-MAINTAINER.md) page.

## CI tests

Before publishing, a set of simple tests were performed on an exhaustive
set of platforms. The results are available from:

- [GitHub Actions](https://github.com/xpack-dev-tools/patchelf-xpack/actions/)
- [Travis CI](https://app.travis-ci.com/github/xpack-dev-tools/patchelf-xpack/builds/)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
c79162020bcd3fc32bb4c70e87384ae98e629a8e083f0410dd77fa59273c8bd2
xpack-patchelf-0.18.0-1-darwin-arm64.tar.gz

7c41af0c72ed1c6bf27f57124ce3fa503bb94910f469613beb58cafb913df70a
xpack-patchelf-0.18.0-1-darwin-x64.tar.gz

a9b7ea8b688e612b33a499a25d9a7b7eb939c2f2f4aae873c1025238ecea9895
xpack-patchelf-0.18.0-1-linux-arm.tar.gz

1caf13e06cbf3c256e8796b48d8277d178111576d0172fa41c879435515d1a1e
xpack-patchelf-0.18.0-1-linux-arm64.tar.gz

563da19b560b159815e85b3358c4fe3fb3c81985f8c3a010f9dc038b6f707d1a
xpack-patchelf-0.18.0-1-linux-x64.tar.gz

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

## Pre-deprecation notice for Ubuntu 18.04

Ubuntu 18.04 LTS _Bionic Beaver_ reached the end of the standard five-year
maintenance window for Long-Term Support (LTS) release on 31 May 2023.

As a courtesy, the xPack GNU/Linux releases will continue to be based on
Ubuntu 18.04 for another year.

From 2025 onwards, the GNU/Linux binaries will be built on **Debian 10**,
(**GLIBC 2.28**), and are also expected to run on RedHat 8.

Users are urged to update their build and test infrastructure to
ensure a smooth transition to the next xPack releases.

## Download analytics

- GitHub [xpack-dev-tools/patchelf-xpack](https://github.com/xpack-dev-tools/patchelf-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/patchelf-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/patchelf-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/patchelf-xpack/total.svg)](https://github.com/xpack-dev-tools/patchelf-xpack/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=patchelf-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/patchelf](https://www.npmjs.com/package/@xpack-dev-tools/patchelf)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/patchelf.svg)](https://www.npmjs.com/package/@xpack-dev-tools/patchelf/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/patchelf.svg)](https://www.npmjs.com/package/@xpack-dev-tools/patchelf/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
