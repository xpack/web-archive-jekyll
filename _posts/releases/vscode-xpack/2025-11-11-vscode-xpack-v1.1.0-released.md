---

title:  VS Code xPack extension v1.1.0 released
sidebar: vscode

summary: "Version **1.1.0** is a new minor release of **ilg-vscode.xpack**; it improves the rendering of the actions/scripts tree."

version: 1.1.0

date: 2024-11-11 23:38:00 +0200

comments: true

categories:
  - releases
  - vscode-xpack

tags:
  - releases
  - vscode
  - vscode-xpack
  - extension
  - c++

---

## Install

The **VS Code xPack C/C++ Managed Build Extension** is
available as **ilg-vscode.xpack** from the
[Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ilg-vscode.xpack).

It can also be installed from a terminal:

```sh
code --install-extension ilg-vscode.xpack
```

This specific version can be installed with the following command,
although generally it is recommended to use the latest version:

```sh
code --install-extension ilg-vscode.xpack@{{ page.version }}
```

## Changes

The {{ page.version }} release
is generally compatible with previous releases.

### Bug fixes

- none

### Enhancements

- none

### Other changes

- [[#49](https://github.com/xpack/vscode-xpack-extension-ts/issues/49)]: for workspaces with multiple folders, group packages by folder names.
- [[#50](https://github.com/xpack/vscode-xpack-extension-ts/issues/50)]: show npm scripts in the xpack tree.

### Known problems

- none

## Supported platforms

The **ilg-vscode.xpack** extension is fully portable and works on any
platform supported by VS Code; internally it relies on **xpm**, which
is also a portable application running on all platforms supported
by **npm**/**node**.

However, for projects using binary xpm packages, they are available mainly
on the modern platforms, like Windows/macOS/Linux.
