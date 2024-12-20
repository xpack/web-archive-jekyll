---
title:  xPack GNU Arm Embedded GCC v9.3.1-1.3 released
sidebar: arm-none-eabi-gcc

summary: "Version **9.3.1-1.3** is a maintenance release of **xPack GNU Arm Embedded GCC**, created with the new, more robust, build scripts."

arm_version: 9-2020-q2-update
arm_date: June 01, 2020
version: 9.3.1-1.3
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/releases/v9.3.1-1.3/

date: 2020-10-12 09:52:00 +0300

redirect_to: https://xpack-dev-tools.github.io/arm-none-eabi-gcc-xpack/blog/2020/10/12/arm-none-eabi-gcc-v9-3-1-1-3-released/

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
  - c++
  - exceptions

---

The [xPack GNU Arm Embedded GCC](https://xpack.github.io/dev-tools/arm-none-eabi-gcc/)
is the **xPack** distribution of the
[GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm).

There are separate binaries for **Windows** (x64 and x86),
**macOS** (x64) and **GNU/Linux** (x64 and x86, arm64 and arm).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

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
**{{ page.arm_version }}** release {{ page.arm_date }} and it is based on the
`gcc-arm-none-eabi-{{ page.arm_version }}-src.tar.bz2` source invariant.

For more details see the original Arm release text files:

- `distro-info/arm-readme.txt`
- `distro-info/arm-release.txt`

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

## Changes

Compared to the official Arm version, there should be no functional changes.

Starting with 9.x, the new archives are created with
a single folder named `xpack-arm-none-eabi-gcc-9.3.1-1.3` instead of
the hierarchical `xPacks/arm-none-eabi-gcc/9.3.1-1.3`. This internal
folder name is used consistently on all platforms. The archive extension
was changed to `.tar.gz`.

With these changes, the archives can now be used directly in other
development environments (like Arduino), without having to repack them.

### Python

Support for Python scripting was added to GDB. This distribution provides
a separate binary, `arm-none-eabi-gdb-py3` with
support for **Python 3.7**.

It is mandatory to have **exactly** this version installed, otherwise
GDB will not start properly.

For this it is recommended to install the binaries provided by
[Python](https://www.python.org/downloads/),
not those available in the distribution, since they may be incomplete, for
example those in Ubuntu/Debian, which split the Python system library into
multiple packages.

On GNU/Linux, the recommended way is to build is from sources, and
install locally:

```bash
python3_version="3.7.9"
mkdir -p "${HOME}/Downloads"
curl -L --fail -o "${HOME}/Downloads/Python-${python3_version}.tgz" https://www.python.org/ftp/python/${python3_version}/Python-${python3_version}.tgz
rm -rf "${HOME}/Work/Python-${python3_version}"
mkdir -p "${HOME}/Work"
cd "${HOME}/Work"
tar xzf "${HOME}/Downloads/Python-${python3_version}.tgz"
cd "${HOME}/Work/Python-${python3_version}"
bash ./configure --prefix="${HOME}/opt"
make
make altinstall
```

To run GDB with this version of Python, use a script to set the proper
environment, like:

```bash
mkdir -p "${HOME}/opt/bin"
cat <<'__EOF__' > "${HOME}/opt/bin/arm-none-eabi-gdb-py3.sh"
#!/usr/bin/env bash
PYTHONPATH="$($HOME/opt/bin/python3.7 -c 'import os; import sys; print(os.pathsep.join(sys.path))')" \
PYTHONHOME="$($HOME/opt/bin/python3.7 -c 'import sys; print(sys.prefix)')" \
arm-none-eabi-gdb-py3 "$@"
__EOF__
chmod +x "${HOME}/opt/bin/arm-none-eabi-gdb-py3.sh"
```

Support for Python 2 was discontinued.

### Text User Interface (TUI)

Support for TUI was added to GDB. The `ncurses` library (v6.2) was added to
the distribution.

{% include note.html content="TUI is not available on Windows." %}

## Bug fixes

- none

## Enhancements

- none

## Known problems

- the GDB binary with Python support was built with version 3.7,
  and require exactly this version in order to run properly; fixed in
  9.3.1-1.4 which includes the Python run-time;
- GDB may issue the following warning, _arm-none-eabi-gdb: warning:
  Couldn't determine a path for the index cache directory._;
  it is a known problem, caused when trying to create the cache
  folder (`$HOME/.cache/gdb` or `$HOME/Library/Caches/gdb`);

## Shared libraries

On all platforms the packages are standalone, and expect only the standard
runtime to be present on the host.

All dependencies that are build as shared libraries are copied locally in the
same folder as the executable.

### `DT_RPATH` and `LD_LIBRARY_PATH`

On GNU/Linux the binaries are adjusted to use a relative path:

```console
$ readelf -d library.so | grep rpath
 0x000000000000001d (RPATH)            Library runpath: [$ORIGIN]
```

In the GNU ld.so search strategy, the `DT_RPATH` has
the highest priority, higher than `LD_LIBRARY_PATH`, so if this later one
is set in the environment, it should not interfere with the xPack binaries.

Please note that previous versions, up to mid-2020, used `DT_RUNPATH`, which
has a priority lower than `LD_LIBRARY_PATH`, and does not tolerate setting
it in the environment.

### `@executable_path`

Similarly, on macOS, the binaries are adjusted with `otool` to use a
relative path.

## Documentation

The original PDF documentation is available in the `share/doc` folder.

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
[README-MAINTAINER](https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack/blob/xpack/README-MAINTAINER.md) page.

## Travis tests

The first set of tests were performed on Travis, by running
a simple script to check if the binaries start and compile several simple
programs on a wide range of platforms and distributions:

- [test xPack Arm Embed GCC on stable platforms](https://travis-ci.org/github/xpack-dev-tools/arm-none-eabi-gcc-xpack/builds/735017027)
- [test xPack Arm Embed GCC on latest platforms](https://travis-ci.org/github/xpack-dev-tools/arm-none-eabi-gcc-xpack/builds/735026750)

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
f22f0d49c27f844dcfe629a6a33878d767b6945acd7508d9578b20b17b106f4c
xpack-arm-none-eabi-gcc-9.3.1-1.3-darwin-x64.tar.gz

9a9e96b9ac3634d7632d35aa0d8138f8468d4f3f4d752374a95420ff7c8e4476
xpack-arm-none-eabi-gcc-9.3.1-1.3-linux-arm64.tar.gz

0e6720296f291141cd757d90e6bf60867a1232de9abc52b0cde28af12eeb94f2
xpack-arm-none-eabi-gcc-9.3.1-1.3-linux-arm.tar.gz

1950c7b0b4e35bacec32450158ec192ac469189a5fb27c2fd7c01e9603e50e64
xpack-arm-none-eabi-gcc-9.3.1-1.3-linux-x32.tar.gz

9045d261b000d921887fc801427542eed2df1616f63a2969a2640f8be2593686
xpack-arm-none-eabi-gcc-9.3.1-1.3-linux-x64.tar.gz

7432cfff045dc421d2ba177c3777ec1e82d4febe5f5f51fb2e90ff07d27cd466
xpack-arm-none-eabi-gcc-9.3.1-1.3-win32-x32.zip

bb2370eb70678cec6d6251d2fad2570539bd2e1884e181e350c2e124ec2dcfdf
xpack-arm-none-eabi-gcc-9.3.1-1.3-win32-x64.zip
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
