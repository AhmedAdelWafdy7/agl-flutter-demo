# Flutter AGL Demo

A simple Flutter application for Automotive Grade Linux (AGL) that displays your name and a button to show an image.

## Overview

This repository contains a Flutter application specifically designed to run on the AGL platform. The application demonstrates integration of Flutter with AGL's salmon branch. It features a minimal UI that displays a name and a button that, when clicked, toggles the visibility of an image.

## Features

- Simple Flutter UI optimized for automotive displays
- Integration with AGL framework
- Button-activated image display
- Easily customizable codebase

## Prerequisites

To build and deploy this application, you will need:

- Ubuntu 22.04 LTS (Jammy Jellyfish)
- Git
- Python 3 and pip
- [meta-flutter/workspace-automation](https://github.com/meta-flutter/workspace-automation)
- Yocto Project tooling
- AGL salmon branch


# AGL Flutter Demo

A Flutter application demo for Automotive Grade Linux (AGL).

## AGL Integration Details

Following steps were taken to integrate this app into AGL image.

### 1. Build AGL locally
The 'agl-ivi-demo-flutter' of AGL branch was built locally and tested using QEMU.

### 2. Add Yocto recipe for our flutter app
Under the `recipes-demo` folder I created a new directory named `agl-flutter-demo`. The agl-flutter-demo has `.bb` file containing following recipe:

```
SUMMARY = "AGL Flutter Demo Application"
HOMEPAGE = "https://github.com/AhmedAdelWafdy7/agl-flutter-demo"
LICENSE = "CLOSED"
SECTION = "graphics"
PV = "1.0+git${SRCREV}"
SRC_URI = "git://github.com/AhmedAdelWafdy7/agl-flutter-demo.git;protocol=https;branch=main"
SRCREV = "${AUTOREV}"
S = "${WORKDIR}/git"

inherit flutter-app agl-app

PUBSPEC_APPNAME = "agl_flutter_demo"
PUBSPEC_IGNORE_LOCKFILE = "1"
FLUTTER_APPLICATION_INSTALL_PREFIX = "/usr/share/flutter"
AGL_APP_TEMPLATE = "agl-app-flutter"
AGL_APP_NAME = "AGL Flutter Demo"
AGL_APP_ID = "agl_flutter_demo"
```

### 3. Build the image again
In order for our changes to be reflected we need to re-build the updated recipes and then build the entire image again. Following commands will achieve this:

```
$ source agl-init-build-env
$ bitbake agl-flutter-demo
$ bitbake agl-ivi-demo-flutter
```

This will take a couple of minutes depending upon system speed.

### 4. Running our image using qemu
Now it's time to see if our newly added app works as intended or not. We'll run the following command to boot the image:

```
$ runqemu kvm serialstdio slirp publicvnc
```

The AGL image is running in background, we can use Vinagre to open it. The "AGL Flutter Demo" should be visible inside the AGL interface.

### 5. Demo
[Screencast from 03-15-2025 10:23:33 PM.webm](https://github.com/user-attachments/assets/ab91c02b-759f-4ff9-9a11-8fee507e398f)


## Acknowledgments

- [Automotive Grade Linux (AGL)](https://www.automotivelinux.org/)
- [Flutter](https://flutter.dev/)
- [meta-flutter](https://github.com/meta-flutter)

## Screenshots
![remmina_localhost:0_localhost:0_20250315-202258](https://github.com/user-attachments/assets/1595d66f-2323-4e32-8148-d17403f757fd)


![remmina_localhost:0_localhost:0_20250315-202304](https://github.com/user-attachments/assets/07aceb9e-c3ed-4064-8290-04f80345b446)

![remmina_localhost:0_localhost:0_20250315-202309](https://github.com/user-attachments/assets/123f67ed-1717-4a09-8b10-99a437d31189)

