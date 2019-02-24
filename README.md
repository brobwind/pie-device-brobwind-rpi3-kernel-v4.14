### Kernel for Raspberry Pi 3 to boot Android 9 Pie

#### Setup build environment
Assuming you already downloaded Android 9 Pie source code and the device configuration files
from https://github.com/brobwind/pie-device-brobwind-rpi3.

And already built the whole project.

#### Download source code
Download the source code from https://github.com/brobwind/pie-device-brobwind-rpi3-kernel-v4.14
```bash
$ git clone -b pie-device-brobwind-rpi3 https://github.com/brobwind/pie-device-brobwind-rpi3-kernel-v4.14 kernel-v4.14
```

#### Build
Assuming current path is kernel-v4.14, execute following commands will build a 64-bit kernel.
1. Run configuration
```bash
$ export INSTALL_ROOT=`pwd`/../device/brobwind/rpi3/boot/kernel-v4.14
$ export CROSS_COMPILE=`pwd`/../prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin/aarch64-linux-androidkernel-
$ INSTALL_PATH=${INSTALL_ROOT} INSTALL_MOD_PATH=${INSTALL_ROOT} ARCH=arm64 make bcmrpi3_defconfig
```

2. Build kernel image
```bash
$ INSTALL_PATH=${INSTALL_ROOT} INSTALL_MOD_PATH=${INSTALL_ROOT} ARCH=arm64 make -j 4
```

3. Build dtbs
```bash
$ INSTALL_PATH=${INSTALL_ROOT} INSTALL_MOD_PATH=${INSTALL_ROOT} ARCH=arm64 make -j 4 dtbs
```

#### Install target
The kernel image and the dtbs will be installed in device/brobwind/rpi3/boot/kernel-v4.14 after executing follow commands:
```bash
$ INSTALL_PATH=${INSTALL_ROOT} INSTALL_MOD_PATH=${INSTALL_ROOT} ARCH=arm64 make dtbs_install
$ INSTALL_PATH=${INSTALL_ROOT} INSTALL_MOD_PATH=${INSTALL_ROOT} ARCH=arm64 make install
```
NOTE: Install dtbs before kernel
