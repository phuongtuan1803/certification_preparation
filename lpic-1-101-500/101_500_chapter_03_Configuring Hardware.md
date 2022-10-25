# LPIC-1: Chapter 3: Configuring Hardware

## ========================= COURSE =======================

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 1

## ========================= MAIN =========================

```bash
# Device Interfaces
#  PCI Boards 
#     - Internal hard drives:
#           + Parallel Advanced Technology Attachment (PATA) : /dev/hdx
#           + Serial Advanced Technology Attachment(SATA)    : /dev/sdx
#           + Small Computer System Interface (SCSI)         : /dev/sdx
#     - External hard drives:  host bus adapter (HBA)
#     - Network interface cards
#     - Wireless cards
#     - Bluetooth devices
#     - Video accelerators
#     - Audio cards
#  The USB Interface 
#  The GPIO Interface 

# System files
#  /dev: 
#     - Character device files
#     - Block device files
#  /proc:
#     - Interrupt Requests (IRQs): $ cat /proc/interrupts
#     - I/O Ports                : $ sudo cat /proc/ioports
#     - Direct Memory Access     : $ cat /proc/dma
#  /sys:
$ sudo lsdev  # dev
$ lsblk       # block device
$ lsblk -S    # (SCSI)
$ lspci
$ lsusb

```

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
# The udev program 
#     - runs in the background at all times and automatically detects new hardware connected to the running
#     - creates persistent device files for storage devices.
#          + /dev/disk/by-id
#          + /dev/disk/by-label
#          + /dev/disk/by-path
#          + /dev/disk/by-uuid
# 
# Multipath
# ■ dm-multipath: The kernel module that provides multipath support
# ■ multipath: A command-line command for viewing multipath devices
# ■ multipathd: A background process for monitoring paths and activating/deactivating paths
# ■ kpartx: A command-line tool for creating device entries for multipath storage devices
# Logical Volume Manager 
#     - Volume Group
#     - Physical Volume
#     - Logical Volume 
# ■ pvcreate : Creates a physical volume
# ■ vgcreate : Groups physical volumes into a volume group
# ■ lvcreate: Creates a logical volume from partitions in each physical volume 
# 
# Partitioning Tools
# fdisk
# gdisk
# parted

# Filesystems
# Directory   Description
# /boot       Contains boot loader files used to boot the system
# /etc        Contains system and application configuration files
# /home       Contains user data files
# /media      Used as a mount point for removable devices
# /mnt        Also used as a mount point for removable devices
# /opt        Contains data for optional third-party programs
# /tmp        Contains temporary files created by system users
# /usr        Contains data for standard Linux programs
# /usr/bin    Contains local user programs and data
# /usr/local  Contains data for programs unique to the local installation
# /usr/sbin   Contains data for system programs and data
# /var        Contains variable data files, including system and application logs
# 
# Linux Filesystems
# ■ btrfs
# ■ ecryptfs
# ■ ext3
# ■ ext4
# ■ reiserFS
# ■ swap
# Creating Filesystems
$ sudo mkfs -t ext4 /dev/sdb1
#  Mounting Filesystems : Manually
$ sudo mount -t ext4 /dev/sdb1 /media/usb1 
$ mount
#  Mounting Filesystems : Automatically
$ cat /etc/fstab
# ■ df : Displays disk usage by partition
# ■ du : Displays disk usage by directory; good for finding users or applications that are taking up the most disk space
# ■ iostat : Displays a real-time chart of disk statistics by partition
# ■ lsblk : Displays current partition sizes and mount points 
#  Filesystem Tools 
# ■ blkid : Display information about block devices, such as storage drives
# ■ chattr : Change file attributes on the filesystem
# ■ debugfs : Manually view and modify the filesystem structure, such as undeleting a file or extracting a corrupted file
# ■ dumpe2fs : Display block and superblock group information
# ■ e2label : Change the label on the filesystem
# ■ resize2fs : Expand or shrink a filesystem
# ■ tune2fs : Modify filesystem parameters 
$ sudo fsck -f /dev/sdb1

Linux system
# dbus desktop bus : interprocess communication software bus
# - system bus
# - session bus
udevadm
dbus-monitor
```

```bash
# kernel modules
$ lsmod
$ modinfo bluetooth
$ sudo insmod [*.ko] # the kernel module files are stored in the /lib/modules 
$ sudo modprobe -rv btusb # remove
$ sudo modprobe -iv btusb # info

udevadm
dbus-monitor
modinfo video
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
