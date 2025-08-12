---

title:  VS Code xPack extension v1.0.1 released
sidebar: vscode

summary: "Version **1.0.1** is the first major release of **ilg-vscode.xpack**; it updates the project to ES6 modules."

version: 1.0.1

date: 2024-02-20 14:47:00 +0300

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

- the project was updated and now can be built as an ES6 module, allowing
to update its dependencies to modules too
- [[#47](https://github.com/xpack/vscode-xpack-extension-ts/issues/47)]: the
actions tree was renamed **XPM ACTIONS**.

### Known problems

- none

## Supported platforms

The **ilg-vscode.xpack** extension is fully portable and works on any
platform supported by VS Code; internally it relies on **xpm**, which
is also a portable application running on all platforms supported
by **npm**/**node**.

However, for projects using binary xPacks, they are available mainly
on the modern platforms, like Windows/macOS/Linux.
