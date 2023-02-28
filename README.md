# Edimax-ac1200-usb-wifi-adaper-driver-for-linux
It is based on [official source code](https://www.edimax.com/edimax/download/download/data/edimax/global/download/wireless_adapters_ac1200_dual-band/ew-7822uac) and some compiling problems was fixed when Linux kernel version above 5.11.
The driver has been tested on Ubuntu 22.04.1 (5.15.0-58-generic) and Ubuntu 22.04.2 (5.19.0-32-generic), and works well.

# Compile

```bash
sudo apt install build-essential

sudo apt install linux-headers-$(uname -r) # raspberrypi: sudo apt install raspberrypi-kernel-headers

cd /path/to/edimax-ac1200-usb-driver-for-linux

make
```

# Install and uninstall
## Temporary install
```bash
cd /path/to/edimax-ac1200-usb-driver-for-linux

sudo insmod xxx.ko

```

## Uninstall
```bash
sudo rmmod xxx.ko
```

## Automatically install when kernel updated
```bash
sudo apt install dkms

cd /path/to/edimax-ac1200-usb-driver-for-linux

touch dkms.conf

cat << EOF >> dkms.conf
PACKAGE_NAME="rtl8812au"
PACKAGE_VERSION="1.0.0"
BUILT_MODULE_NAME[0]="8812au"
MAKE="'make' all"
CLEAN="'make' clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"
EOF

sudo mv /path/to/edimax-ac1200-usb-driver-for-linux /usr/src/rtl8812au-1.0.0  # move the directory to `/usr/src/` and rename it to rtl8812au-1.0.0

sudo dkms add -m rtl8812au -v 1.0.0

sudo dkms build -m rtl8812au -v 1.0.0

sudo dkms install -m rtl8812au -v 1.0.0

sudo dkms status # confirm that the setting of dkms for driver successful.

```

## Uninstall
```bash
sudo dkms remove -m rtl8812au -v 1.0.0 --all

sudo status # confirm remove successfully

cd /usr/src

sudo rm -rf rtl8812au-1.0.0

```
