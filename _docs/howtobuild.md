---
title: How to build
permalink: /docs/howtobuild/
---

You will need arm-linux-gnueabi and aarch64-linux-gnu toolchains. [Linaro](https://releases.linaro.org/components/toolchain/binaries/latest-7/) have working toolchains.

## Build `coreboot.rom`

Clone and build [u-boot](https://github.com/lakka-switch/u-boot) : 

```
cd u-boot
export CROSS_COMPILE=aarch64-linux-gnu-
make nintendo-switch_defconfig
make
```

Clone and build [coreboot](https://github.com/lakka-switch/coreboot) : 

```
cd coreboot
make nintendo_switch_defconfig
make iasl
make
```

You will need to put `tegra_mtc.bin` in `src/soc/nvidia/tegra210`. The output is `coreboot/build/coreboot.rom`.

## Build the payload

Clone and build [shofel2](https://github.com/lakka-switch/shofel2) : 

```
cd shofel2/exploit
make
```

The output is `shofel2/exploit/cbfs.bin`.

## Build Lakka

The first build can take between four and eight hours depending on your internet and computer speed. Be prepared.

Clone and build [Lakka-LibreELEC](https://github.com/lakka-switch/Lakka-LibreELEC) :

```
cd Lakka-LibreELEC
DISTRO=Lakka PROJECT=Switch ARCH=aarch64 make image
```

The output kernel, system image, update package and full SD card image will be placed in the `target` directory.
