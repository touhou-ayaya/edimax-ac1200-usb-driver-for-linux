# Edimax-ac1200-usb-wifi-adaper-driver-for-linux
It isn't an official support, but based on [official source code](https://www.edimax.com/edimax/download/download/data/edimax/global/download/wireless_adapters_ac1200_dual-band/ew-7822uac) and some compiling problems was fixed when Linux kernel version above 5.11.
The driver has been tested on Ubuntu 22.04.1 (5.15.0-58-generic), and works well.

# Edimax ac1200 usb wifi驱动
这不是官方支持。但基于[官方的源码](https://www.edimax.com/edimax/download/download/data/edimax/global/download/wireless_adapters_ac1200_dual-band/ew-7822uac)，解决了在Linux内核版本5.11以上时，一些驱动编译的问题。
该驱动已在Ubuntu 22.04.1上测试，并可以正常的使用。

# Compile

```bash
sudo apt install build-essential
sudo apt install linux-headers-$(uname -r) # raspberrypi: sudo apt install raspberrypi-kernel-headers
make
```
