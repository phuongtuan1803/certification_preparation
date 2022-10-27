# Basic Configuring Hardware

## Device Interfaces

- Device Interfaces: PCI(Peripheral Component Interconnect) Boards
  - Internal hard drives:
    - Parallel Advanced Technology Attachment (PATA) : /dev/hdx
    - Serial Advanced Technology Attachment(SATA)    : /dev/sdx
    - Small Computer System Interface (SCSI)         : /dev/sdx
  - External hard drives:  host bus adapter (HBA)
  - Network interface cards
  - Wireless cards
  - Bluetooth devices
  - Video accelerators
  - Audio cards
- The USB Interface
- The GPIO Interface

| COMMANDS    | OPTIONS                                               |     |
| ----------- | ----------------------------------------------------- | --- |
| dmidecode   | **DMI table decoder**                                 |     |
|             | -t, --type TYPE                                       |     |
|             | -q, --quite                                           |     |
|             | -s, --string KEYWORD                                  |     |
| lshw        | **list hardware**                                     |     |
|             | -html, -xml, -json                                    |     |
|             | -short                                                |     |
|             | -businfo                                              |     |
|             | -numeric                                              |     |
|             | -C, -class class                                      |     |
| lspci       | **list all PCI devices**                              |     |
|             | -v, -vv, -vvv                                         |     |
|             | -s [[[[<domain>]:]<bus>]:][<device>][.[<func>]]       |     |
|             | **ex**: lspci -s 00:00.0                              |     |
| lsscsi      | **list SCSI devices (or hosts) and their attributes** |     |
| usb-devices | **print USB device details**                          |     |
| lsusb       | **list USB devices**                                  |     |
|             | -v, --verbose                                         |     |
|             | -s [[bus]:][devnum]                                   |     |
|             | -d [vendor]:[product]                                 |     |
|             | -D device                                             |     |
|             | **ex**: lsusb -s 002:001                              |     |
| blkid       | **locate/print block device attributes**              |     |
| lsblk       | **list block devices**                                |     |
|             | -a, --all                                             |     |
|             | -S, --SCSI                                            |     |
|             | -p, --paths                                           |     |
|             | -m, --perms                                           |     |
| lscpu       | **display information about the CPU architecture**    |     |
| lsdev       | **list devices**                                      |     |
|             |                                                       |     |
TODO: lsdev is not in CentOS
**NOTE:**

- dmesg | grep usb
- gdisk -l /dev/sda
- hdparm -I /dev/sda

## System files

- /dev:
  - Character device files
  - Block device files
- /proc:
  - Interrupt Requests (IRQs): $ cat /proc/interrupts
  - I/O Ports                : $ sudo cat /proc/ioports
  - Direct Memory Access     : $ cat /proc/dma
- /sys:

## Hardware Modules

| COMMANDS | OPTIONS                                                                                         |     |
| -------- | ----------------------------------------------------------------------------------------------- | --- |
| lsmod    | **Show the status of modules in the Linux Kernel**                                              |     |
|          |                                                                                                 |     |
| modinfo  | **Show information about a Linux Kernel module**                                                |     |
|          |                                                                                                 |     |
| insmod   | **Simple program to insert a module into the Linux Kernel**                                     |     |
|          | **insmod [filename] [module options...]**                                                       |     |
|          | **ex**: insmod vboxvideo.ko                                                                     |     |
|          |                                                                                                 |     |
| modprobe | **Add and remove modules from the Linux Kernel**                                                |     |
|          | **modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-b] [modulename] [module parameters...]** |     |
|          | **modprobe [-r] [-v] [-n] [-i] [modulename...]**                                                |     |
|          | **modprobe [-c]**                                                                               |     |
|          | **modprobe [--dump-modversions] [filename]**                                                    |     |
|          | **ex**: sudo modprobe -iv btusb                                                                 |     |
|          | -a, --all                                                                                       |     |
|          | -C, --config                                                                                    |     |
|          | -i, --ignore-install, --ignore-remove                                                           |     |
|          | -r, --remove                                                                                    |     |
|          | -v, --verbose                                                                                   |     |
|          | -q, --quiet                                                                                     |     |
| depmod   | **Generate modules.dep and map files**                                                          |     |
|          |                                                                                                 |     |

## Storage Basics

### Types of Drives

- Parallel Advanced Technology Attachment (PATA) : /dev/hdx
- Serial Advanced Technology Attachment(SATA)    : /dev/sdx
- Small Computer System Interface (SCSI)         : /dev/sdx

### Drive Partitions

A partition is a self-contained section within the drive that the operating system treats as a separate storage space

- BIOS bootloader use master boot record (MBR):
  - only up to four primary partitions on a drive
  - primary partition can be split into multiple extended partitions.
  - MBR extended partitions are numbered starting at 5
  - 2 TB
- UEFI bootloader use GUID Partition Table (GPT)
  - supports up to 128 partitions on a drive
  - partitions starting with number 1
  - 18 EB

Technology

- BIOS partition
  - by BIOS
  - only 4 partition
  - 1 partition become an extended partition (contains logical drivea)
  - cannot boot from logical drive
- GUID partition
  - GUID partition table (GPT)
  - no 4 partition, no extented patition, no logical drives
- LVM partition (Logical Volume Management)
  - abtraction layer above real patitions or disks


### Automatic Drive Detection

The udev program

- runs in the background at all times and automatically detects new hardware connected to the running
- creates persistent device files for storage devices.
  - /dev/disk/by-id
  - /dev/disk/by-label
  - /dev/disk/by-path
  - /dev/disk/by-uuid

| COMMANDS     | OPTIONS                                                                                                                          |     |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------- | --- |
| udevadm      | **udev management tool**                                                                                                         |     |
|              | **udevadm [--debug] [--version] [--help]**                                                                                       |     |
|              | **udevadm info options**                                                                                                         |     |
|              | **udevadm trigger [options]**                                                                                                    |     |
|              | **udevadm settle [options]**                                                                                                     |     |
|              | **udevadm control command**                                                                                                      |     |
|              | **udevadm monitor [options]**                                                                                                    |     |
|              | **udevadm test [options] devpath**                                                                                               |     |
|              | **udevadm test-builtin [options] command devpath**                                                                               |     |
|              |                                                                                                                                  |     |
| dbus-monitor | **debug probe to print message bus messages**                                                                                    |     |
|              | **dbus-monitor [--system \| --session \| --address ADDRESS] [--profile \| --monitor \| --pcap \| --binary] [watch expressions]** |     |
|              | **ex**: sudo dbus-monitor --system                                                                                               |     |

## Storage Alternatives

### Device Mapper (DM) Multipath

- dm-multipath: The kernel module that provides multipath support
- multipath: A command-line command for viewing multipath devices
- multipathd: A background process for monitoring paths and activating/deactivating paths
- kpartx: A command-line tool for creating device entries for multipath storage devices
<!-- TODO -->
Use dynamic /dev/mapper device file directory

### Logical Volume Manager

Logical Volume Manager

- Physical Volume
- Volume Group
- Logical Volume
  
| LVM               |                   |                   |
| ----------------- | ----------------- | ----------------- |
| Disk A            | Disk A            | Disk B            |
| Physical Volume 1 | Physical Volume 2 | Physical Volume 3 |
| Volume Group 1    | Volume Group 2    | Volume Group 2    |
| Logical Volume 1  | Logical Volume 2  | Logical Volume 3  |

| COMMANDS  | OPTIONS                                                                  |     |
| --------- | ------------------------------------------------------------------------ | --- |
| pvcreate  | **Initialize physical volume(s) for use by LVM**                         |     |
|           | **pvcreate position_args [ option_args ]**                               |     |
|           | **ex:** pvcreate /dev/sdc4 /dev/sde                                      |     |
|           |                                                                          |     |
| vgcreate  | **Create a volume group**                                                |     |
|           | **vgcreate position_args [ option_args ]**                               |     |
|           | **ex:** vgcreate myvg /dev/sdk1 /dev/sdl1                                |     |
|           |                                                                          |     |
| lvcreate  | **Create a logical volume**                                              |     |
|           | **lvcreate option_args position_args [ option_args ] [ position_args ]** |     |
|           | **ex:** lvcreate -n projects -L 10G vg0                                  |     |
|           | **ex:** lvcreate -n backups -l 100%FREE vg0                              |     |
|           | -n, --name String                                                        |     |
|           | -l, --extents Number[PERCENT]                                            |     |
|           | -L, --size Size[m\|UNIT]                                                 |     |
|           |                                                                          |     |
| pvs       | **Display information about physical volumes**                           |     |
| vgs       | **Display information about volume groups**                              |     |
| lvs       | **Display information about logical volumes**                            |     |
| pvdisplay | **Display various attributes of physical volume(s)**                     |     |
| vgdisplay | **Display volume group information**                                     |     |
| lvdisplay | **Display information about a logical volume**                           |     |

**NOTE:**

- Guide for parted command: $ sudo parted
    1. print all
    2. print devices
    3. select /dev/sdc
    4. mklabel msdos
    5. mkpart primary 1 500MB
    6. quit

- Guide for resize a partition
    1. note of old partition boundaries
      sudo mkdir /media/sdb1
      sudo mount /dev/sdb1 /media/sdb1
      lsblk
    2. delete old partition
    3. create new larger partition
    4. resize the file system
      sudo gdisk /dev/sdb
          - p # print
          - d
          - n
          - w
      sudo umount /dev/sdb1
      sudo partprobe
      sudo mkfs -t ext4 /dev/sdb1
      sudo mount /dev/sdb1 /media/sdb1

    5. verify
      lsblk
      df -h
      resize2fs /dev/sdb1

- Guild for create Logical Volume of LVM:

    sudo umount /dev/sdb1
    sudo pvcreate /dev/sdb1
    sudo pvs
    sudo vgcreate vgdata /dev/sdb1
    sudo vgs
    sudo lvcreate --name lvdata --size 500M vgdata
    sudo lvs
    
    sudo mkfs -t ext4 /dev/vgdata/lvdata
    sudo blkid

- Guild for extend Volume Group of LVM:
    sudo vgextend vgdata /dev/sdc1
    sudo vgresize -l 100%FREE /dev/vgdata/lvdata
    resize2fs /dev/vgdata/lvdata

- Guild for reduce Volume Group of LVM:
    sudo umount /dev/vgdata/lvdata
    sudo e2fsck -ff /dev/vgdata/lvdata

    sudo resize2fs /dev/vgdata/lvdata 500M
    sudo lvresize -L 500M /dev/vgdata/lvdata
    sudo mount /dev/vgdata/lvdata /media/lvdata

    sudo lvresize -r -L 400M /dev/vgdata/lvdata
    df -h
    sudo lvresize -r -L 600M /dev/vgdata/lvdata
    df -h

- Guild for Replace physiscal Volume of LVM:
    sudo lvresize -r -l 100%VG /dev/vgdata/lvdata
    sudo pvmov /dev/sdc1 /dev/sdd1
    sudo pvreduce vgdata /dev/sdc1

- backup
    sudo dump -0uf /home/lvdata.dump /dev/vgdata/lvdata
    sudo dump -0uf /home/lvdata.dump /dev/vgdata/lvdata | ssh user@hostname "dd of=lvdata.dump"
    sudo restore -rf /home/lvdata.dump

### Redundant Array of Inexpensive Disks (RAID) Technology

RAID technology allows you to improve data access performance and reliability, as well as implement data redundancy for fault tolerance by combining multiple drives into one virtual drive

### Partitioning Tools

| COMMANDS  | OPTIONS                                                                    |                                                |
| --------- | -------------------------------------------------------------------------- | ---------------------------------------------- |
| fdisk     | **manipulate disk partition table**                                        |                                                |
|           | **fdisk [-uc] [-b sectorsize] [-C cyls] [-H heads] [-S sects] device**     |                                                |
|           | **fdisk -l [-u] [device...]**                                              |                                                |
|           | **fdisk -s partition...**                                                  |                                                |
|           | **fdisk -v**                                                               |                                                |
|           | **fdisk -h**                                                               |                                                |
|           | **ex:** fdisk /dev/sda                                                     |                                                |
|           | -l device                                                                  | List the partition tables                      |
|           |                                                                            |                                                |
| gdisk     | **Interactive GUID partition table (GPT) manipulator**                     |                                                |
|           | **gdisk [ -l ] device**                                                    |                                                |
|           | **ex:** gdisk /dev/sda                                                     |                                                |
|           | -l device                                                                  | List the partition tables                      |
|           |                                                                            |                                                |
| parted    | **a partition manipulation program**                                       |                                                |
|           | **parted [options] [device [command [options...]...]]**                    |                                                |
|           | **ex:** parted /dev/sda                                                    |                                                |
|           |                                                                            |                                                |
| partprobe | **inform the OS of partition table changes**                               |                                                |
|           | **partprobe [-d] [-s] [devices...]**                                       |                                                |
|           | -d                                                                         | Don't update the kernel                        |
|           | -s                                                                         | Show a summary of devices and their partitions |
|           |                                                                            |                                                |
| sfdisk    | **partition table manipulator for Linux**                                  |                                                |
| cfdisk    | **display or manipulate disk partition table**                             |                                                |
| sgdisk    | **Command-line GUID partition table (GPT) manipulator for Linux and Unix** |                                                |
| cgdisk    | **Curses-based GUID partition table (GPT) manipulator**                    |                                                |

## Filesystems

### Common Linux FHS directories|

| Directory  | Description                                                         |
| ---------- | ------------------------------------------------------------------- |
| /boot      | Contains boot loader files used to boot the system                  |
| /etc       | Contains system and application configuration files                 |
| /home      | Contains user data files                                            |
| /media     | Used as a mount point for removable devices                         |
| /mnt       | Also used as a mount point for removable devices                    |
| /opt       | Contains data for optional third-party programs                     |
| /tmp       | Contains temporary files created by system users                    |
| /usr       | Contains data for standard Linux programs                           |
| /usr/bin   | Contains local user programs and data                               |
| /usr/local | Contains data for programs unique to the local installation         |
| /usr/sbin  | Contains data for system programs and data                          |
| /var       | Contains variable data files, including system and application logs |

### Formatting Filesystems

#### Common Filesystem Types

Linux Filesystems

- btrfs
- ecryptfs
- ext3
- ext4
- reiserFS
- swap

Non-Linux Filesystems

- CIFS
- exFAT
- HFS
- ISO-9660
- NFS
- NTFS
- UDF
- VFAT
- XFS
- ZFS

#### Creating Filesystems

| COMMANDS | OPTIONS                                                 |     |
| -------- | ------------------------------------------------------- | --- |
| mkfs     | **build a Linux filesystem**                            |     |
|          | **mkfs [options] [-t type] [fs-options] device [size]** |     |
|          | **ex**:  mkfs -t ext4 /dev/sdb1                         |     |
|          | -t, --type type                                         |     |
|          | -V, --verbose                                           |     |

#### Mounting Filesystems

| COMMANDS | OPTIONS                                                  |                                                                |
| -------- | -------------------------------------------------------- | -------------------------------------------------------------- |
| mount    | **mount a filesystem**                                   |                                                                |
|          | **mount [-lhV]**                                         |                                                                |
|          | **mount -a [-fFnrsvw] [-t vfstype] [-O optlist]**        |                                                                |
|          | **mount [-fnrsvw] [-o option[,option]...]  device\|dir** |                                                                |
|          | **mount [-fnrsvw] [-t vfstype] [-o options] device dir** |                                                                |
|          | **ex**:  mount -t ext4 /dev/sdb1 /media/usb1             |                                                                |
|          | -a, --all                                                | Mount all filesystems (of the given types) mentioned in fstab. |
|          |                                                          |                                                                |
| umount   | **unmount a filesystem**                                 |                                                                |
|          | **umount [-hV]**                                         |                                                                |
|          | **umount -a [-dflnrv] [-t vfstype] [-O options]**        |                                                                |
|          | **umount [-dflnrv] {dir\|device}...**                    |                                                                |
Mounting Filesystems : Manually
sudo mount -t ext4 /dev/sdb1 /media/usb1
mount

Mounting Filesystems : Automatically
cat /etc/fstab

#### Managing Filesystems

##### Retrieving Filesystem Stats

| COMMANDS | OPTIONS                                                                                                    |     |
| -------- | ---------------------------------------------------------------------------------------------------------- | --- |
| df       | **report file system disk space usage**                                                                    |     |
|          | **df [OPTION]... [FILE]...**                                                                               |     |
|          | -a, --all                                                                                                  |     |
|          | --total                                                                                                    |     |
|          | -h, --human-readable                                                                                       |     |
|          | -t, --type=TYPE                                                                                            |     |
|          | -x, --exclude-type=TYPE                                                                                    |     |
|          | -T, --print-type                                                                                           |     |
|          |                                                                                                            |     |
| du       | **estimate file space usage**                                                                              |     |
|          | **du [OPTION]... [FILE]...**                                                                               |     |
|          | **du [OPTION]... --files0-from=F**                                                                         |     |
|          | -a, --all                                                                                                  |     |
|          | -c, --total                                                                                                |     |
|          | -d, --max-depth=N                                                                                          |     |
|          | -h, --human-readable                                                                                       |     |
|          | -s, --summarize                                                                                            |     |
|          |                                                                                                            |     |
| iostat   | **Report Central Processing Unit (CPU) statistics and input/output statistics for devices and partitions** |     |
|          | **ex:** iostat -x sda sdb 2 6       - Display six reports at two second intervals for all devices          |     |
|          | -c     Display the CPU utilization report                                                                  |     |
|          | -d     Display the device utilization report                                                               |     |
|          | -x     Display extended statistics                                                                         |     |
|          | -h     human readable                                                                                      |     |
| lsblk    | **list block devices**                                                                                     |     |
|          | -a, --all                                                                                                  |     |
|          | -S, --SCSI                                                                                                 |     |
|          | -p, --paths                                                                                                |     |
|          | -m, --perms                                                                                                |     |
|          |                                                                                                            |     |

##### Filesystem Tools

blkid : Display information about block devices, such as storage drives
chattr : Change file attributes on the filesystem
debugfs : Manually view and modify the filesystem structure, such as undeleting a file or extracting a corrupted file
dumpe2fs : Display block and superblock group information
e2label : Change the label on the filesystem
resize2fs : Expand or shrink a filesystem
tune2fs : Modify filesystem parameters

| COMMANDS | OPTIONS                                                                                  |                                             |
| -------- | ---------------------------------------------------------------------------------------- | ------------------------------------------- |
| fsck     | **check and repair a Linux filesystem**                                                  |                                             |
|          | **fsck [-lrsAVRTMNP] [-C [fd]] [-t fstype] [filesystem...]  [--] [fs-specific-options]** |                                             |
|          | **ex**: sudo fsck -f /dev/sdb1                                                           |                                             |
|          | -A                                                                                       | check all filesystemsin /etc/fstab          |
|          | -R                                                                                       | with the -A flag, skip the root filesystem. |
|          | -a                                                                                       | Automatically  repair                       |
|          | -y                                                                                       | attempt to fix                              |
|          | -n                                                                                       | attempt to not fix                          |
|          |                                                                                          |                                             |
|          |                                                                                          |                                             |
