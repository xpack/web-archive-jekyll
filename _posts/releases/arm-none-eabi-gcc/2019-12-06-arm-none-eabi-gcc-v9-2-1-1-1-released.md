---
title:  xPack GNU Arm Embedded GCC v9.2.1-1.1 released
sidebar: arm-none-eabi-gcc

summary: "Version **9.2.1-1.1** is a new release of **xPack GNU Arm Embedded GCC**, following Arm release from November 06, 2019 (version **9-2019-q4-major**)."

version: 9.2.1-1.1
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/releases/v9.2.1-1.1/

date: 2019-12-06 16:07:00 +0200

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2019/12/06/arm-none-eabi-gcc-v9-2-1-1-1-released/

comments: true

categories:
  - releases
  - arm-none-eabi-gcc

tags:
  - releases
  - arm
  - arm-none-eabi-gcc
  - gcc
  - binaries

---

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Install

The full details of installing the **xPack GNU Arm Embedded GCC** on
various platforms are presented in the separate [Install]({{ site.baseurl }}/dev-tools/arm-none-eabi-gcc/install/) page.

### Easy install

The easiest way to install GNU Arm Embedded GCC is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/arm-none-eabi-gcc`](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc)
from the [`npmjs.com`](https://www.npmjs.com) registry.

To install the latest version available, use:

```sh
xpm install --global @xpack-dev-tools/arm-none-eabi-gcc@latest --verbose
```

To install this specific version, use:

```sh
xpm install --global @xpack-dev-tools/arm-none-eabi-gcc@{{ page.version }}.{{ page.npm_subversion }}
```

## Compliance

This release follows the official
[GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm)
**9-2019-q4-major** release from November 06, 2019 and it is based on the
`gcc-arm-none-eabi-9-2019-q4-major-src.tar.bz2` source invariant.

For more details see the original Arm release text files:

- `distro-info/arm-readme.txt`
- `distro-info/arm-release.txt`

{% include note.html content="Compared to the Arm distribution, the Aarch64 binaries are not yet available." %}

## Supported libraries

The supported libraries are:

```console
$ arm-none-eabi-gcc -print-multi-lib
.;
arm/v5te/softfp;@marm@march=armv5te+fp@mfloat-abi=softfp
arm/v5te/hard;@marm@march=armv5te+fp@mfloat-abi=hard
thumb/nofp;@mthumb@mfloat-abi=soft
thumb/v7/nofp;@mthumb@march=armv7@mfloat-abi=soft
thumb/v7+fp/softfp;@mthumb@march=armv7+fp@mfloat-abi=softfp
thumb/v7+fp/hard;@mthumb@march=armv7+fp@mfloat-abi=hard
thumb/v7-r+fp.sp/softfp;@mthumb@march=armv7-r+fp.sp@mfloat-abi=softfp
thumb/v7-r+fp.sp/hard;@mthumb@march=armv7-r+fp.sp@mfloat-abi=hard
thumb/v6-m/nofp;@mthumb@march=armv6s-m@mfloat-abi=soft
thumb/v7-m/nofp;@mthumb@march=armv7-m@mfloat-abi=soft
thumb/v7e-m/nofp;@mthumb@march=armv7e-m@mfloat-abi=soft
thumb/v7e-m+fp/softfp;@mthumb@march=armv7e-m+fp@mfloat-abi=softfp
thumb/v7e-m+fp/hard;@mthumb@march=armv7e-m+fp@mfloat-abi=hard
thumb/v7e-m+dp/softfp;@mthumb@march=armv7e-m+fp.dp@mfloat-abi=softfp
thumb/v7e-m+dp/hard;@mthumb@march=armv7e-m+fp.dp@mfloat-abi=hard
thumb/v8-m.base/nofp;@mthumb@march=armv8-m.base@mfloat-abi=soft
thumb/v8-m.main/nofp;@mthumb@march=armv8-m.main@mfloat-abi=soft
thumb/v8-m.main+fp/softfp;@mthumb@march=armv8-m.main+fp@mfloat-abi=softfp
thumb/v8-m.main+fp/hard;@mthumb@march=armv8-m.main+fp@mfloat-abi=hard
thumb/v8-m.main+dp/softfp;@mthumb@march=armv8-m.main+fp.dp@mfloat-abi=softfp
thumb/v8-m.main+dp/hard;@mthumb@march=armv8-m.main+fp.dp@mfloat-abi=hard
```

## Bug fixes

- none,

## Changes

There should be no functional changes.

Compared to previous releases, the new archives are created with
a single folder named `xpack-arm-none-eabi-gcc-9.2.1-1.1` instead of
the hierarchical `xPacks/arm-none-eabi-gcc/9.2.1-1.1`. This internal
folder name is used consistently on all platforms. The archive extension
was changed to `.tar.gz`.

With these changes, the archives can now be used directly in other
development environments (like Arduino), without having to repack them.

### Python 3

Partial experimental support for Python 3 was added to GDB for GNU/Linux
and macOS; not yet available on Windows
([24469](https://sourceware.org/bugzilla/show_bug.cgi?id=24469)).

## Known problems

- [[#5]](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/issues/5)
the `arm-none-eabi-gdb-py` fails to start on Ubuntu (and possibly
other Debian) systems, it fails with a message like:
```console
$ PYTHONHOME=/usr PYTHONPATH=/usr/lib/python2.7 arm-none-eabi-gdb-py --version
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 554, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 536, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 587, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 533, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 417, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
```

The problem is caused by gdb-py not being able to locate the Python
system libraries, split into multiple packages and installed in multiple
folders.

The workaround is to pass the Python environment to gdb-py:

```bash
PYTHONPATH="$(python -c 'import os; import sys; print(os.pathsep.join(sys.path))')" \
PYTHONHOME="$(python -c 'import sys; print(sys.prefix)')"
```

- C++ exceptions in the non-nano libraries are not caught; fixed in
 9.3.1-1.2.

## Documentation

The original PDF documentation is available in the `share/doc` folder.

## Supported platforms

Binaries for **Windows**, **macOS** and **GNU/Linux** are provided.

The binaries were built using the
[xPack Build Box (XBB)](https://github.com/xpack/xpack-build-box), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

- x86/x64 GNU/Linux: all binaries were built with GCC 7.4, running in a CentOS 6
  Docker container
- x86/x64 Windows: all binaries were built with mingw-w64 GCC 7.4, running in a
  CentOS 6 Docker container
- x64 macOS: most binaries were built with GCC 7.4, running in a separate
  folder on macOS 10.10.5; GDB cannot be compiled with GCC, so Apple
  clang was used.

## Tests

The binaries were testes on Windows 10 Pro 32/64-bit, Ubuntu 18 LTS 64-bit,
Xubuntu 18 LTS 32-bit and macOS 10.13.

The tests consist in building and debugging some
[simple Eclipse projects](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/tree/xpack/tests/eclipse)
available in the project.

Since the source code used for GCC is identical to the one used by Arm, the
long and complex tests performed by Arm to validate their release were not
executed again.

## Checksums

The SHA-256 hashes for the files are:

```txt
6ff68117083624273c56244cf4242989a65069b376a9727ec4a230be824340f3
xpack-arm-none-eabi-gcc-9.2.1-1.1-darwin-x64.tar.gz

e9f4b5f3ebe7e4391e2423e4106493d7cfcdee9eee4a1f0766f1c23662093a49
xpack-arm-none-eabi-gcc-9.2.1-1.1-linux-x32.tar.gz

bbde117b97f229dfe63721c0323c3da6839e83cf302c8f4ff25e0f36ecf7a428
xpack-arm-none-eabi-gcc-9.2.1-1.1-linux-x64.tar.gz

d13aaff4caae6e5f1b871d50accc1759c4f5750574dbd4d6f6e3017c33f39dc6
xpack-arm-none-eabi-gcc-9.2.1-1.1-win32-x32.zip

923bf50198cb155361a95fcac8804d12acd64e963a89f352c69fe24bf54ff0ef
xpack-arm-none-eabi-gcc-9.2.1-1.1-win32-x64.zip
```

## Download analytics

- GitHub [xpack-dev-tools/arm-none-eabi-gcc-xpack](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/arm-none-eabi-gcc-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/arm-none-eabi-gcc-xpack/total.svg)](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/releases/)
  - all GNU MCU Eclipse releases [![Github All Releases](https://img.shields.io/github/downloads/gnu-mcu-eclipse/arm-none-eabi-gcc/total.svg)](https://github.com/gnu-mcu-eclipse/arm-none-eabi-gcc/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=arm-none-eabi-gcc-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/arm-none-eabi-gcc](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/arm-none-eabi-gcc.svg)](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/arm-none-eabi-gcc.svg)](https://www.npmjs.com/package/@xpack-dev-tools/arm-none-eabi-gcc/)
  - all @gnu-mcu-eclipse releases [![npm](https://img.shields.io/npm/dt/@gnu-mcu-eclipse/arm-none-eabi-gcc.svg)](https://www.npmjs.com/package/@gnu-mcu-eclipse/arm-none-eabi-gcc/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
