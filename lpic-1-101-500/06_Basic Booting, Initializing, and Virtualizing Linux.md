# Basic Booting, Initializing, and Virtualizing Linux

## Boot Process

1. Firmware stage:

- execute code from BIOS or UEFI
- execute bootloader code (GRUB2) (BIOS: GRUB Write data to MBR (Master Boot Record))

2. Bootloader stage:

- read its configuration file

3. Kernel stage:

- load RAMDisk -> RAM
- load devive drivers from RAMDisk
- load config files from RAMDisk
- unmounts RAMDisk
- mounts root filesystem

4. Initialization stage

- start grandfather process (Upstart, SysVinit, systemd)
- systemd start system services
- systemd start login shells and GUI interfaces
   Note: default targer is "graphical.target"

## Firmware stage: GRUB

| COMMANDS          | OPTIONS                                        |     |
| ----------------- | ---------------------------------------------- | --- |
| grub2-install     | **Install GRUB on a device**                   |     |
|                   |                                                |     |
| grub2-mkconfig    | **Generate a GRUB configuration file**         |     |
|                   | **ex:** grub2-mkconfig -o /boot/grub2/grub.cfg |     |
|                   |                                                |     |
| grub2-set-default | **Set the default boot menu entry for GRUB**   |     |
|                   | **ex:** grub2-set-default 0                    |     |

**Note:**

- Grub template
    cat /etc/grub.d/40_custom /boot//grub2/grub.cfg > ~/40_custom
- Update kernel
    uname -r
    sudo yum list installed kernel-.*
    sudo yum list available kernel
    sudo yum update kernel

## Firmware stage: Boot screen

 E key: edit kernel script
        at the kernel line (linux*), add
        systemd.unit=emergency # emergency mode
        rd.break               # root mount as readonly
                               # mount -o remount.rw /sysroot
                               # chroot /sysroot
        ctl + x for finish

## Initialization stage: systemd

| COMMANDS      | OPTIONS                                                     |                                                                                        |
| ------------- | ----------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| systemctl     | **Control the systemd system and service manager**          |                                                                                        |
|               | **systemctl [OPTIONS...] COMMAND [NAME...]**                |                                                                                        |
|               | -a, --all                                                   | When listing units, show all loaded units                                              |
|               | -l, --full                                                  | status, list-units, list-jobs, and list-timers                                         |
|               | list-units/list-sockets/list-timers [PATTERN...]            |                                                                                        |
|               | list-unit-files  [PATTERN...]                               | List installed unit files and their enablement state (as reported by is-enabled)       |
|               | -t, --type=                                                 |                                                                                        |
|               | --state=                                                    |                                                                                        |
|               |                                                             |                                                                                        |
|               | cat PATTERN...                                              | Show backing files of one or more units                                                |
|               | is-active/is-failed/is-enabled                              |                                                                                        |
|               | start/stop/restart/disable/enable                           |                                                                                        |
|               | mark/unmark                                                 |                                                                                        |
|               | get-default                                                 | Return the default target to boot into                                                 |
|               | set-default NAME                                            | Set the default target to boot into                                                    |
|               | isolate NAME                                                | Start the unit specified on the command line and its dependencies and stop all others. |
|               | **ex:** systemclt isolate multi-user.target                 |                                                                                        |
|               | daemon-reload                                               | Reload systemd manager configuration                                                   |
|               |                                                             |                                                                                        |
| systemd-delta | **Find overridden configuration files**                     |                                                                                        |
|               | **systemd-delta [OPTIONS...] [PREFIX[/SUFFIX]\|SUFFIX...]** |                                                                                        |
**Note:**
    - systemclt is the service start at first
        ps -p 1

## Logging

| COMMANDS   | OPTIONS                                      |                                                                            |
| ---------- | -------------------------------------------- | -------------------------------------------------------------------------- |
| rsyslog    | **reliable and extended syslogd**            |                                                                            |
| dmesg      | **print or control the kernel ring buffer**  |                                                                            |
| journalctl | **Query the systemd journal**                |                                                                            |
|            | **journalctl [OPTIONS...] [MATCHES...]**     |                                                                            |
|            | **ex:** journalctl /sbin/crond               |                                                                            |
|            | **ex:** journalctl --since yesterday --until |                                                                            |
|            | **ex:** journalctl -b 2                      |                                                                            |
|            | **ex:** journalctl -u crond                  |                                                                            |
|            | -u, --unit=UNIT\|PATTERN                     | Show messages for the specified systemd unit UNIT (such as a service unit) |
|            | -f, --followq                                |                                                                            |
|            | -n, --lines=                                 |                                                                            |
|            | -b [ID][±offset], --boot=[ID][±offset]       | Show messages from a specific boot, 1(1st boot), -0(last boot)             |
|            | -S, --since=, -U, --until=                   |                                                                            |
|            | -k, --dmesg                                  | Show only kernel messages                                                  |
|            | -o, --output=                                | short,verbose,json, cat...                                                 |
|            |                                              |                                                                            |

**Note:**

- rsyslog
    sudo systemctl start rsyslog
    sudo systemctl enable rsyslog
    less -N /etc/rsyslog.conf
    sudo tail -f /var/log/message
  - Structure
    - Global directives
    - Templates
    - Output channels
    - Rules(selector + action)

| rsyslog                                        |                                     |     |     |                                                         |
| ---------------------------------------------- | ----------------------------------- | --- | --- | ------------------------------------------------------- |
| **selector**                                   |                                     |     |     | **action**                                              |
| **facility**                                   | **priority**                        |     |     |                                                         |
| auth, authpriv, cron, daemon, kern, lpr        | debug, info, notice, warning/warn   |     |     | Regular file: file;RSYSLOG_TraditionalFileFormat        |
| mail,  mark, news,  security  (same  as  auth) | error/err, crit, alert, panic/emerg |     |     | Named pipes (create by mkfifo)                          |
| syslog, user, uucp, local0-local7              |                                     |     |     | Terminal and console: tty                               |
|                                                |                                     |     |     | Remote machine: @192.168.0.1 (UDP), @@192.168.0.1 (TCP) |
|                                                |                                     |     |     | Discard: ~                                              |

- journald: reset after reboot
    sudo systemctl start systemd-journald

## Initialization stage: SysVinit

1. Kernel run /sbin/init (grandfather process)
2. Init loads /etc/inittab
3. Inittab configures
        - default level
        - ctrl + alt + del
        - execute links in /etc/rc.d/rc.<runlevel>
4. runlevel scripts start services
        - runlevel 0 - halt
        - runlevel 1 - single-user mode
        - runlevel 2 - multi-user mode
        - runlevel 3 - multi-user mode with networking
        - runlevel 4 - undefined
        - runlevel 5 - multi-user mode with networking and GUI
        - runlevel 6 - reboot

## Virtualizing

### Hypervisor

- Type 1: App -> VM with Guest OS -> Hypervisor ->  Physiscal
- Type 2: App -> VM with Guest OS -> Hypervisor -> Host OS -> Physiscal

### Type of Virtualization

- Emulation
- ParaVirualization (PV)
- Full Virtualization, hardware vitual machine (HVM)
- Full (HVM + PV) with paravirtualized driver
- Hybrid virtualization

### Virtual Machine

1. Install/config a base VM
2. Create a clone of VM
   1. Hypervisor clone commands

3. Create a bare CM
4. Bootstrap the VM
   1. Installation source
   2. Provisioning data
   3. Bootstrap setup
      - create VM with unique MAC address
      - inject data to boot process
      - cloud-init
        1. Generator
           - systemd run cloud-init.target
        2. Local
           - systemd run cloud-init-local.service
        3. Network
           - process user data
           - Setup disks
           - Mount volumes
           - run commands
        4. Config
           - systemd run cloud-config.service
           - run cloud-init configuration modules
        5. Final
           - systemd run cloud-final.service
           - install OS software
           - start the configuration management system
           - run user scripts
5. Configure the VM

- start the configuration management system
- reboot

### Install Media Kernel

inst.ks=<path-to-centos7.bin>
