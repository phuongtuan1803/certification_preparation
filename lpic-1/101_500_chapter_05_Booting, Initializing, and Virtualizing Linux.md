# LPIC-1: Chapter 5: Booting, Initializing, and Virtualizing Linux

## ========================= COURSE =======================

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 2 & 3 & 6 & 12

## ========================= MAIN =========================

```bash
# Boot Process
# 1. Firmware stage: 
#  - execute code from BIOS or UEFI
#  - execute bootloader code (GRUB2) (GRUB Write data to MBR (Master Boot Record))
#    
#    Legacy GRUB
#    - Write data to MBR (Master Boot Record)
# 2. Bootloader stage: 
#  - read its configuration file 
# 3. Kernel stage: 
#  - load RAMDisk -> RAM
#  - load devive drivers from RAMDisk
#  - load config files from RAMDisk
#  - unmounts RAMDisk
#  - mounts root filesystem
# 4. Initialization stage
#  - start grandfather process (Upstart, SysVinit, systemd)
#  - systemd start system services
#  - systemd start login shells and GUI interfaces
#    Note: default targer is "graphical.target"

# GRUB
grub2-install
grub2-mkconfig -o /boot/grub2/grub.cfg
grub2-set-default 0
cat /etc/grub.d/40_custom /boot//grub2/grub.cfg > ~/40_custom

# Kernel
uname -r
sudo yum list installed kernel-.*
sudo yum list available kernel
sudo yum update kernel
```

```bash
# Initialization stage: systemd
ps -p 1
systemctl list-units [-a] [-t service/target] [--state running]
systemctl list-unit-files [-a] [-t service/target] 

systemctl cat/is-active/is-enabled [service name]
systemctl start/stop/restart/disable/enable [service name]
systemclt mark/unmark [service name]

man -k systemd
systemctl get-default # default target
systemctl set-default graphical.target
systemcll isolate multi-user.target
systemd-delta 
systemctl daemon-reload

# Boot screen
# E key: edit kernel script
#        at the kernel line (linux*), add
#        systemd.unit=emergency # emergency mode
#        rd.break               # root mount as readonly
#                               # mount -o remount.rw /sysroot
#                               # chroot /sysroot
#        ctl + x for finish
```

```bash
# Logging: rsyslogd
sudo systemctl start rsyslog
sudo systemctl enable rsyslog
less -N /etc/rsyslog.conf
sudo tail -f /var/log/message

# Logging: journald
#    - reset after reboot
sudo systemctl start systemd-journald
journalctl [-k]
journalctl /sbin/crond
journalctl -u crond
journalctl -f
journalctl -b 2
journalctl --since yesterday --until

```

```bash
# Initialization stage: SysVinit
# 1. Kernel run /sbin/init (grandfather process)
# 2. Init loads /etc/inittab
# 3. Inittab configures
#         - default level
#         - ctrl + alt + del
#         - execute links in /etc/rc.d/rc.<runlevel>
# 4. runlevel scripts start services
#         - runlevel 0 - halt
#         - runlevel 1 - single-user mode
#         - runlevel 2 - multi-user mode
#         - runlevel 3 - multi-user mode with networking
#         - runlevel 4 - undefined
#         - runlevel 5 - multi-user mode with networking and GUI
#         - runlevel 6 - reboot
```

```bash
# Virtualizing
# Hypervisor
#  - Type 1: App -> VM with Guest OS -> Hypervisor ->  Physiscal
#  - Type 2: App -> VM with Guest OS -> Hypervisor -> Host OS -> Physiscal
# Type of Virtualization
#  - Emulation
#  - ParaVirualization (PV)
#  - Full Virtualization, hardware vitual machine (HVM)
#  - Full (HVM + PV) with paravirtualized driver
#  - Hybrid virtualization
# 
# Virtual Machine
# 1. Install/config a base VM
# 2. Create a clone of VM
#  - Hypervisor clone commands
# 3. Create a bare CM
# 4. Bootstrap the VM
#    1. Installation source
#    2. Provisioning data
#    3. Bootstrap setup
#       - create VM with unique MAC address
#       - inject data to boot process
#       - cloud-init
#         1. Generator
#            - systemd run cloud-init.target
#         2. Local
#            - systemd run cloud-init-local.service
#         3. Network
#            - process user data
#            - Setup disks
#            - Mount volumes
#            - run commands
#         4. Config
#            - systemd run cloud-config.service
#            - run cloud-init configuration modules
#         5. Final
#            - systemd run cloud-final.service
#            - install OS software
#            - start the configuration management system
#            - run user scripts
# 5. Configure the VM
#  - start the configuration management system
#  - reboot
# 
# Install Media Kernel
# inst.ks=<path-to-centos7.bin>
```

```bash
# === Partition
# 
# Technology
#   - BIOS partition
#       - by BIOS
#       - only 4 partition
#       - 1 partition become an extended partition (contains logical drivea)
#       - cannot boot from logical drive
#   - GUID partition
#        - GUID partition table (GPT)
#        - no 4 partition, no extented patition, no logical drives
#   - LVM partition (Logical Volume Management)
#        - abtraction layer above real patitions or disks
# 
# Encryption
# 
# Virtual Memory (swap space)
# 
# == Legacy System
#  - Boot with BIOS
#  - Master Boot Record (MBR)
#  - 4 real primary patitions
#  - 2 TB
# 
# Comamnd
fdisk -l [/dev/sdb]
sfdisk
cfdisk
# 
# == Mordern System
#  - Boot with UEFI
#  - GPT (GUID Partition Table)
#  - Unlimited patitions
#  - 18 EB
# 
# Comamnd
gdisk [-l /dev/sdb]
sgdisk
cgdisk
# Comamnd list
lsblk
blkid
# Command create new partition
parted
    - print all
    - print devices
    - select /dev/sdc
    - mklabel msdos
    - mkpart primary 1 500MB
    - quit
# Command resize a partition
# 1. note of old partition boundaries
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
lsblk
# 2. delete old partition
# 3. create new larger partition
# 4. resize the file system
sudo gdisk /dev/sdb
    - p # print
    - d
    - n
    - w
sudo umount /dev/sdb1
sudo partprobe
sudo mkfs -t ext4 /dev/sdb1
sudo mount /dev/sdb1 /media/sdb1
# 5. verify
lsblk
df -h
resize2fs /dev/sdb1

# === LVM
sudo umount /dev/sdb1
sudo pvcreate /dev/sdb1
sudo pvs
sudo vgcreate vgdata /dev/sdb1
sudo vgs
sudo lvcreate --name lvdata --size 500M vgdata
sudo lvs

sudo vgchange -al
sudo mkfs -t ext4 /dev/vgdata/lvdata
sudo blkid

# extend
sudo vgextend vgdata /dev/sdc1
sudo vgresize -l 100%FREE /dev/vgdata/lvdata
resize2fs /dev/vgdata/lvdata
# reduce
sudo umount /dev/vgdata/lvdata
sudo e2fsck -ff /dev/vgdata/lvdata
sudo resize2fs /dev/vgdata/lvdata 500M
sudo lvresize -L 500M /dev/vgdata/lvdata
sudo mount /dev/vgdata/lvdata /media/lvdata
sudo lvresize -r -L 400M /dev/vgdata/lvdata
df -h
sudo lvresize -r -L 600M /dev/vgdata/lvdata
df -h

# Replace physiscal volume (drives)
sudo lvresize -r -l 100%VG /dev/vgdata/lvdata
sudo pvmov /dev/sdc1 /dev/sdd1
sudo pvreduce vgdata /dev/sdc1


# === filesystem
# 
sudo unmount /dev/vgdata/lvdata # ext2
mkfs /dev/vgdata/lvdata
sudo tune2fs /dev/vgdata/lvdata # ext3
sudo mount -t ext4 /dev/vgdata/lvdata /media/lvdata # ext4

# Repair
sudo mount /dev/vgdata/lvdata /media/lvdata
df -h
sudo cp -rvf / /media/lvdata
# ctl + c to corupt
sudo dd if=/dev/zero bf=1 count=10 of=/dev/vgdata/lvdata seek=1000
sudo unmount /media/lvdata
sudo fsck -n /dev/vgdata/lvdata # expect have corruption
fsck [-A] [-R] [-f] [-a] [-y] [-n]

e2label /dev/sdc1 backup
# edit /etc/fstab 
sudo mount -a
df -h

# backup
sudo dump -0uf /home/lvdata.dump /dev/vgdata/lvdata
sudo dump -0uf /home/lvdata.dump /dev/vgdata/lvdata | ssh user@hostname "dd of=lvdata.dump"
sudo restore -rf /home/lvdata.dump 
```

## ========================= FILES ========================

```bash
# BIOS
/flashboot/grub2/grub.cfg
# GRUB
/etc/default/grub
/etc/grub.d
/boot/grub/grub.cfg (generate by grub2-mkconfig)
/boot/grub2/grub.cfg (generate by grub2-mkconfig)
# systemd
/etc/systemd/system/default.target
/etc/systemd/system/graphical.target
/etc/systemd/system/multi-user.target
# journald
/var/run
/var/log/journal
# Kickstart
/root/anaconda-ks.cfg
# Partition
/proc/partitions
/dev/<VolumeGroupName>/<LogiccalVolumeName>
/dev/mapper/<VolumeGroupName>-<LogiccalVolumeName>
example:
    /dev/vgdata/lvdata
    /dev/mapper/vgdata-lvdata
# filesystem
/sbin/mk*
/etc/fstab 
# UUID=<ID>    /media/lvdata    ext3    default    0    0
# LABEL=<label>    /media/lvdata    ext3    default    0    0
```

## ========================= PRACTICE ====================

```bash
systemd
rsyslog
journalctl
logger
```
