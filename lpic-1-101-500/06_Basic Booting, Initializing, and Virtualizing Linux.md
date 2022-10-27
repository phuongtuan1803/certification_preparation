# Basic Booting, Initializing, and Virtualizing Linux

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
dmesg
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
