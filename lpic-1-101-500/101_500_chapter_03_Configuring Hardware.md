# LPIC-1: Chapter 3: Configuring Hardware

## ========================= COURSE =======================

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 1

## ========================= MAIN =========================

```bash
# Hardware resource
lshw
lshw [-short] [-class processor]
lshw -html > /tmp/ouput.html

lscpu
lspci [-vvv] [-v] [-s device_number]
dmidecode -t memory
free -m
lsblk
gdisk -l /dev/sda
blkid
hdparm -I /dev/sda
```

```bash
# USB
lsusb
usb-devices
dmesg | grep usb
```

```bash
# sysfs,dbius, udev
# dbus desktop bus : interprocess communication software bus
# - system bus
# - session bus
udevadm
dbus-monitor
```

```bash
# kernel modules
udevadm
dbus-monitor
lsmod
modinfo video
modprobe [-v] [-r] dm_mirror
depmod -v
```

```bash
# Network Interface
nmtui
nmcli c reload
nmcli dev disconnect enp0s3
nmcli dev up enp0s3
nmcli con show [--active]
nmcli general status
nmcli con edit
```

## ========================= FILES ========================

```bash
/proc/meminfo
/sys
/etc/udev/rules.d
/dev
/lib/modules/$(uname -r)/kernel
/etc/modules-load.d/
/etc/modprobe.d/

/etc/sysconfig/network-scripts/ifcfg-enp0s3
```

## ========================= PRACTICE ====================

```bash
man nmcli-examples
```
