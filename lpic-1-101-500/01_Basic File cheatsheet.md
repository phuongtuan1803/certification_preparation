# Basic File Cheatsheet

## FILES

| FILES                                       |                                     |
| ------------------------------------------- | ----------------------------------- |
| /etc/profile                                |                                     |
| /etc/profile.d                              |                                     |
| ~/.bash_profile                             |                                     |
| ~/.bashrc (run /etc/bashrc)                 |                                     |
| /etc/bashrc                                 |                                     |
| /etc/passwd                                 |                                     |
| /etc/shadow                                 | # !!: pw have not set, !: user lock |
| /etc/group                                  |                                     |
| /etc/gshadow                                |                                     |
| /etc/skel                                   |                                     |
| /etc/login.defs                             |                                     |
| /etc/default/useradd                        |                                     |
| /etc/apt/sources.list                       |                                     |
| /etc/apt/sources.list.d/*                   |                                     |
| /etc/yum.conf                               |                                     |
|                                             |                                     |
| /proc/meminfo                               |                                     |
| /sys                                        |                                     |
| /etc/udev/rules.d                           |                                     |
| /dev                                        |                                     |
| /lib/modules/$(uname -r)/kernel             |                                     |
| /etc/modules-load.d/                        |                                     |
| /etc/modprobe.d/                            |                                     |
| /etc/sysconfig/network-scripts/ifcfg-enp0s3 |                                     |
BIOS
/flashboot/grub2/grub.cfg
GRUB
/etc/default/grub
/etc/grub.d
/boot/grub/grub.cfg (generate by grub2-mkconfig)
/boot/grub2/grub.cfg (generate by grub2-mkconfig)
systemd
/etc/systemd/system/default.target
/etc/systemd/system/graphical.target
/etc/systemd/system/multi-user.target
journald
/var/run
/var/log/journal
Kickstart
/root/anaconda-ks.cfg
Partition
/proc/partitions
/dev/<VolumeGroupName>/<LogiccalVolumeName>
/dev/mapper/<VolumeGroupName>-<LogiccalVolumeName>
example:
    /dev/vgdata/lvdata
    /dev/mapper/vgdata-lvdata
filesystem
/sbin/mk*
/etc/fstab 
UUID=<ID>    /media/lvdata    ext3    default    0    0
LABEL=<label>    /media/lvdata    ext3    default    0    0


## ========================= PRACTICE ====================

| FEATURE            |                        |
| ------------------ | ---------------------- |
| less               |                        |
| emacs/nano/vim     |                        |
| top                |                        |
| tmux               | Multiplexing with tmux |
| screen -ls         |                        |
| w                  |                        |
| man nmcli-examples |                        |
| systemd            |                        |
| rsyslog            |                        |
| journalctl         |                        |
| logger             |                        |

## ========================= MISC ====================

| ls        | **list directory contents**                                             |     |
| l-------r | *---------------------------------------------------------------------* | undefined- |
| lstat     | **get file status**                                                     |     |
| lstat64   | **get file status**                                                     |     |
| lstat     | **get symbolic link status**                                            |     |
| lsearch   | **linear search of an array**                                           |     |
| lsearch   | **linear search and update**                                            |     |
| lseek     | **reposition read/write file offset**                                   |     |
| lseek     | **move the read/write file offset**                                     |     |
| lseek64   | **reposition 64-bit read/write file offset**                            |     |
| lslogins  | **display information about known users in the system**                 |     |
| lsmd      | **lsmd**                                                                |     |
| lsmd.conf | **libStorageMgmt daemon lsmd configuration file.**                      |     |
| lsmem     | **list the ranges of available memory with their online status**        |     |
| lslocks   | **list local system locks**                                             |     |
| lsof      | **list open files**                                                     |     |
| lsmcli    | **libStorageMgmt command line interface**                               |     |
| lsns      | **list namespaces**                                                     |     |
| lsinitrd  | **tool to show the contents of an initramfs image**                     |     |
| lsipc     | **show information on IPC facilities currently employed in the system** |     |
| lsmod     | **Show the status of modules in the Linux Kernel**                      |     |
