---
title: How to build
permalink: /docs/howtobuild/
---

Clone and build [Lakka-LibreELEC](https://github.com/lakka-switch/Lakka-LibreELEC) :

```
cd Lakka-LibreELEC
PROJECT=Switch DEVICE=L4T ARCH=aarch64 make image
```

You can use `DEVICE=mainline` to use the mainline kernel instead of L4T (deprecated). Mainline supports `arm` (`armv7`) and `aarch64` architectures. L4T only supports `aarch64`.

You will need arm-linux-gnueabi and aarch64-linux-gnu toolchains. [Linaro](https://releases.linaro.org/components/toolchain/binaries/latest-7/) have working toolchains.

The first build can take between four and eight hours depending on your internet and computer speed. Be prepared. 

Somewhere during the build process process, a script will download and extract `tegra_mtc.bin` for you, directly from Google's servers (credits goes to vgmoose for that).

The output kernel, system image and release tarball will be placed in the `target` directory.
