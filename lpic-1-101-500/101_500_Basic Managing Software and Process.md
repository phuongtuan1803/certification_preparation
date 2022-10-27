# Basic Managing Software and Process Cheatsheet

## Debian

**Package Format**: # PACKAGE-NAME-VERSION-RELEASE_ARCHITECTURE.deb
**ex**: docker_1.5-1build1_amd64.deb

**Package Format**: The four main repositories are:
    Main - Canonical-supported free and open-source software.
    Universe - Community-maintained free and open-source software.
    Restricted - Proprietary drivers for devices.
    Multiverse - Software restricted by copyright or legal issues. 
**ex**: http://vn.archive.ubuntu.com/ubuntu focal/main amd64 Packages

| COMMANDS           | OPTIONS                                      |               |
| ------------------ | -------------------------------------------- | ------------- |
| dpkg               | **package manager for Debian**               |               |
|                    | -R                                           | --recursive   |
|                    | -r                                           | --remove      |
|                    | -P                                           | --purge       |
|                    | **dpkg-deb actions**                         |               |
|                    | -b                                           | --build       |
|                    | -c                                           | --contents    |
|                    | -x                                           | --extract     |
|                    | -X                                           | --vextract    |
|                    | -I                                           | -info archive |
|                    | **dpkg-query actions**                       |               |
|                    | -l                                           | --list        |
|                    | -L                                           | --listfiles   |
|                    | -S                                           | --status      |
| apt-cache          | **query the APT cache**                      |               |
|                    |                                              |               |
|                    |                                              |               |
| apt-cdrom          | **APT CD-ROM management utility**            |               |
|                    |                                              |               |
|                    |                                              |               |
| apt-config         | **APT Configuration Query program**          |               |
|                    |                                              |               |
|                    |                                              |               |
| apt-get            | **APT package handling utility**             |               |
|                    | install --download-only                      |               |
|                    |                                              |               |
| apt                | **command-line interface**                   |               |
|                    | **apt-get**                                  |               |
|                    | update                                       |               |
|                    | upgrade                                      |               |
|                    | full-upgrade                                 |               |
|                    | install, reinstall                           |               |
|                    | remove, purge                                |               |
|                    | autoremove                                   |               |
|                    | satisfy                                      |               |
|                    | **apt-cache**                                |               |
|                    | search                                       |               |
|                    | show                                         |               |
|                    | **other**                                    |               |
|                    | list                                         |               |
|                    | policy                                       |               |
| add-apt-repository | **add-apt-repository [OPTIONS] REPOSITORY**  |               |
|                    | -r                                           | --remove      |
| dpkg-reconfigure   | **reconfigure an already installed package** |               |
|                    | **dpkg-reconfigure [options] packages**      |               |
|                    | -r                                           | --remove      |

## Red Hat

**Package Format**: PACKAGE-NAME-VERSION-RELEASE.ARCHITECTURE.rpm
**ex**: docker-1.13.1-94.gitb2f74b2.el7.centos.x86_64.rpm

| COMMANDS        | OPTIONS                                                         |                                         |
| --------------- | --------------------------------------------------------------- | --------------------------------------- |
| yumdownloader   | **download RPM packages from Yum repositories**                 |                                         |
|                 |                                                                 |                                         |
| rpm             | **RPM Package Manager**                                         |                                         |
|                 | **q\|--query**                                                  |                                         |
|                 | -a, --all                                                       |                                         |
|                 | -p, --package PACKAGE_FILE                                      |                                         |
|                 | --changelog                                                     |                                         |
|                 | --i, --info                                                     |                                         |
|                 | -l, --list                                                      |                                         |
|                 | -d, --docfiles                                                  |                                         |
|                 | -c, --configfiles                                               |                                         |
|                 | -f, --file FILE                                                 |                                         |
|                 | --provides                                                      | List capabilities this package provides |
|                 | -R, --requires                                                  |                                         |
|                 | -s, --state                                                     |                                         |
|                 | **V\|--verify**                                                 |                                         |
|                 | **i\|--install**                                                |                                         |
|                 | **U\|--upgrade**                                                |                                         |
|                 | **F\|--freshen**                                                |                                         |
|                 | **e\|--erase**                                                  |                                         |
| yum             | **Yellowdog Updater Modified**                                  |                                         |
|                 | **yum [options] command [package ...]**                         |                                         |
|                 | --downloadonly                                                  |                                         |
|                 | install                                                         |                                         |
|                 | reinstall                                                       |                                         |
|                 | localinstall                                                    |                                         |
|                 | list                                                            |                                         |
|                 | upgrade                                                         |                                         |
|                 | remove                                                          |                                         |
|                 | autoremove                                                      |                                         |
|                 | clean all                                                       |                                         |
|                 | group [...]                                                     |                                         |
| package-cleanup | **clean up locally installed, duplicate, or orphaned packages** |                                         |
|                 | --leaves                                                        |                                         |
|                 |                                                                 |                                         |
|                 |                                                                 |                                         |
|                 |                                                                 |                                         |
|                 |                                                                 |                                         |

Note:
    - Another way which download only
        yum install -y yum-plugin-downloadonly
        yum install -y --downloadonly --downloaddir=/tmp/packages
    - Create cpio file
        rpm2cpio emacs-24.3-22.el7.x86_64.rpm > emacs.cpio
        cpio -idv < emacs.cpio
    - yum group
        yum group list ids
        yum group install "Security Tools" [--setopt=group_package_types=mandatory,default,optional]
        yum group install security-tools
        yum install @"Security Tools"
        yum install @security-tools

        yum group [remove/autoremove] security-tools
        yum group update security-tools
        yum group info security-tools

## Process

| COMMANDS | OPTIONS                                                  |                                                             |
| -------- | -------------------------------------------------------- | ----------------------------------------------------------- |
| ps       | **report a snapshot of the current processes**           |                                                             |
|          | **ps [options]**                                         |                                                             |
|          | **SIMPLE PROCESS SELECTION**                             |                                                             |
|          | -A, -e                                                   | Select all processes                                        |
|          | -a                                                       | all except session leaders and not associated with terminal |
|          | -d                                                       | all except session leaders                                  |
|          | T                                                        | associated with terminal                                    |
|          | **PROCESS SELECTION BY LIST**                            |                                                             |
|          | p 123, -p 123, --pid 123, -123, 123                      |                                                             |
|          | -C cmdlist                                               | select command name                                         |
|          | -G, --Group grplist                                      | select by real group ID or name                             |
|          | -g, --group grplist                                      | select by session or by effective group name                |
|          | -U, -User userlist                                       | select by real user ID or name                              |
|          | -u, --user userlist                                      | select by session or by effective user name                 |
|          | **OUTPUT FORMAT CONTROL**                                |                                                             |
|          | --format, -o                                             | user-defined format                                         |
|          | -f                                                       | full-format listing                                         |
|          | -F                                                       | Extra full format                                           |
|          | j, -j, l, -l                                             |                                                             |
|          | **OUTPUT MODIFIERS**                                     |                                                             |
|          | c                                                        | show true command name                                      |
|          | -H                                                       | show process hierarchy                                      |
|          | --sort spec                                              |                                                             |
|          | S                                                        | Sum                                                         |
|          | **THREAD DISPLAY**                                       |                                                             |
|          | H                                                        | show threads as if they were process                        |
| free     | **Display amount of free and used memory in the system** |                                                             |
|          | -h, --human                                              |                                                             |
| top      | **display Linux processes**                              |                                                             |
|          |                                                          |                                                             |
**Note**:
    - sum memory of user:
        ps -U grant --format %mem | awk '{memory +=$1};END {print memory}'

## Signal

| Number | Name | Description                                         |
| ------ | ---- | --------------------------------------------------- |
| 1      | HUP  | Hangs up                                            |
| 2      | INT  | Interrupts                                          |
| 3      | QUIT | Stops running                                       |
| 9      | KILL | Unconditionally terminates                          |
| 11     | SEGV | Segments violation                                  |
| 15     | TERM | Terminates if possible                              |
| 17     | STOP | Stops unconditionally, but doesn’t terminate        |
| 18     | TSTP | Stops or pauses, but continues to run in background |
| 19     | CONT | Resumes execution after STOP or TSTP                |

| COMMANDS     | OPTIONS                                                           |            |
| ------------ | ----------------------------------------------------------------- | ---------- |
| kill         | **terminate a process**                                           |            |
|              | **kill [-s signal\|-p] [-q sigval] [-a] [--] pid...**             |            |
|              | **kill -l [signal]**                                              |            |
|              | **ex**: kill -USR1 $(pidof dd)                                    |            |
|              | -s, --signal signal                                               |            |
|              | -l, --list [signal]                                               |            |
|              | -L, --table                                                       | similar -l |
|              | -p, --pid                                                         |            |
|              | -q, --queue sigval                                                |            |
|              | -a, --all                                                         |            |
|              |                                                                   |            |
| killall      | **kill processes by name**                                        |            |
|              | **ex**: killall -u grant                                          |            |
|              | **ex**: killall crond                                             |            |
|              | -g, --process-group                                               |            |
|              | -u, --user                                                        |            |
|              | -r, --regexp                                                      |            |
|              | -q, --quiet                                                       |            |
|              | -I, --ignore-case                                                 |            |
|              | -e, --exact                                                       |            |
| pidof        | **find the process ID of a running program**                      |            |
| pgrep, pkill | **look up or signal processes based on name and other attribute** |            |
|              | -t, --terminal term                                               |            |
|              |                                                                   |            |
|              |                                                                   |            |
|              |                                                                   |            |
|              |                                                                   |            |
|              |                                                                   |            |

## Process Niceness/Priority (-19 -> 19, lower best)

| COMMANDS | OPTIONS                                             |     |
| -------- | --------------------------------------------------- | --- |
| nice     | **run a program with modified scheduling priority** |     |
|          | **ex**: nice -2 top                                 |     |
|          | **ex**: sudo nice --2 top                           |     |
|          | -n, --adjustment=N                                  |     |
|          |                                                     |     |
| renice   | **alter priority of running processes**             |     |
|          | **renice [-n] priority [-gpu] identifier**          |     |
|          | **ex**: renice 5 123                                |     |
|          | -n, --priority priority                             |     |
|          | -g, --pgrp pgid...                                  |     |
|          | -u, --user name_or_uid                              |     |
|          | -p, --pid pid                                       |     |
|          |                                                     |     |

## Forcegroud/Backgroud

| COMMANDS | OPTIONS                                                       |                 |
| -------- | ------------------------------------------------------------- | --------------- |
| nohup    | **run a command immune to hangups, with output to a non-tty** |                 |
|          | **nohup COMMAND [ARG]...**                                    |                 |
| jobs     | **[-lnprs] [ jobspec ... ]**                                  |                 |
|          | -l                                                            | List process ID |
| fg, bg   | **ex**: fg %2                                                 |                 |
|          | **ex**: bg %2                                                 |                 |
|          | **ex**: kill %2                                               |                 |
| watch    | **execute a program periodically, showing output fullscreen** |                 |
|          | **watch [options] command**                                   |                 |
|          | -n, --interval seconds                                        |                 |
|          |                                                               |                 |
|          |                                                               |                 |
|          |                                                               |                 |
|          |                                                               |                 |

## Shared library

|     | Shared library        |                      |
| --- | --------------------- | -------------------- |
| 1   | LD_LIBRARY_PATH       | environment variable |
| 2   | PATH                  | environment variable |
| 3   | /etc/ld.so.conf.d/    | folder               |
| 4   | /etc/ld.so.conf       | file                 |
| 5   | /lib*/ and /usr/lib*/ | folders              |

| COMMANDS | OPTIONS                                                |     |
| -------- | ------------------------------------------------------ | --- |
| ldd      | **print shared library dependencies**                  |     |
|          | **ex**: ldd /usr/bin/echo                              |     |
| locate   | **find files by name**                                 |     |
|          | **ex**: locate ld-linux                                |     |
| updatedb | **update a database for mlocate**                      |     |
| ldconfig | **configure dynamic linker run-time bindings**         |     |
|          | **ex**: ldconfig -v 2> /dev/null\| grep libmysqlclient |     |
