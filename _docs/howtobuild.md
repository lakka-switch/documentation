---
title: How to build
permalink: /docs/howtobuild/
---

You will need arm-linux-gnueabi and aarch64-linux-gnu toolchains. [Linaro](https://releases.linaro.org/components/toolchain/binaries/latest-7/) have working toolchains.

The first build can take between four and eight hours depending on your internet and computer speed. Be prepared. 

Somewhere during the build process process, a script will download and extract `tegra_mtc.bin` for you, directly from Google's servers (credits goes to vgmoose for that).

Clone and build [Lakka-LibreELEC](https://github.com/lakka-switch/Lakka-LibreELEC) :

```
cd Lakka-LibreELEC
DISTRO=Lakka PROJECT=Switch ARCH=aarch64 make image
```

You will encounter an error when compiling Linux, about an issue with `asm` includes. To fix this, delete the `linux-*` directory in the build directory, and try again.

The output kernel, system image and release tarball will be placed in the `target` directory.
