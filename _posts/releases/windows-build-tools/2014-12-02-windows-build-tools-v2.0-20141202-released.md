---
title:  Build Tools repacked as Setup
sidebar: windows-build-tools

download_url: https://github.com/gnu-mcu-eclipse/windows-build-tools/releases/tag/v2.0/
date: 2014-12-02 12:00:00 +0200

comments: true

categories:
  - releases
  - windows-build-tools

tags:
  - releases
  - windows-build-tools
  - windows
  - setup
  - build
  - make
  - rm

---

For your convenience, the [Windows Build Tools]({{ site.baseurl }}/dev-tools/windows-build-tools/) were repacked as a Windows setup.

[Binary files »]({{ page.download_url }})

![Build Tools setup]({{ site.baseurl }}/assets/images/2015/win-build-tools-setup.png)

Please note that the setup does not install any components outside the selected destination folder, and also includes an uninstall program, to completely remove the tools from the system.

The repacking also corrected a problem with the previous archive (the missing DLLs were added), so the previous archive (Cross Build Tools.zip) is now considered DEPRECATE.

For more information, please read the [dedicated page]({{ site.baseurl }}/dev-tools/windows-build-tools/).

## Download

The new Windows Build Tools can be downloaded from the [GitHub Release]({{ page.download_url }}) page.

The available files are:

	Build-Tools-w32-20141202154847-setup.exe
	Cross.Build.Tools.zip


**Cross Build Tools.zip** is included for archiving purposes and is now considered DEPRECATE.
