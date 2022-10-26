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

| COMMANDS           | OPTIONS                                      |               |     |     |
| ------------------ | -------------------------------------------- | ------------- | --- | --- |
| dpkg               | **package manager for Debian**               |               |     |     |
|                    | -R                                           | --recursive   |     |     |
|                    | -r                                           | --remove      |     |     |
|                    | -P                                           | --purge       |     |     |
|                    | **dpkg-deb actions**                         |               |     |     |
|                    | -b                                           | --build       |     |     |
|                    | -c                                           | --contents    |     |     |
|                    | -x                                           | --extract     |     |     |
|                    | -X                                           | --vextract    |     |     |
|                    | -I                                           | -info archive |     |     |
|                    | **dpkg-query actions**                       |               |     |     |
|                    | -l                                           | --list        |     |     |
|                    | -L                                           | --listfiles   |     |     |
|                    | -S                                           | --status      |     |     |
| apt-cache          | **query the APT cache**                      |               |     |     |
|                    |                                              |               |     |     |
|                    |                                              |               |     |     |
| apt-cdrom          | **APT CD-ROM management utility**            |               |     |     |
|                    |                                              |               |     |     |
|                    |                                              |               |     |     |
| apt-config         | **APT Configuration Query program**          |               |     |     |
|                    |                                              |               |     |     |
|                    |                                              |               |     |     |
| apt-get            | **APT package handling utility**             |               |     |     |
|                    | install --download-only                      |               |     |     |
|                    |                                              |               |     |     |
| apt                | **command-line interface**                   |               |     |     |
|                    | **apt-get**                                  |               |     |     |
|                    | update                                       |               |     |     |
|                    | upgrade                                      |               |     |     |
|                    | full-upgrade                                 |               |     |     |
|                    | install, reinstall                           |               |     |     |
|                    | remove, purge                                |               |     |     |
|                    | autoremove                                   |               |     |     |
|                    | satisfy                                      |               |     |     |
|                    | **apt-cache**                                |               |     |     |
|                    | search                                       |               |     |     |
|                    | show                                         |               |     |     |
|                    | **other**                                    |               |     |     |
|                    | list                                         |               |     |     |
|                    | policy                                       |               |     |     |
| add-apt-repository | **add-apt-repository [OPTIONS] REPOSITORY**  |               |     |     |
|                    | -r                                           | --remove      |     |     |
| dpkg-reconfigure   | **reconfigure an already installed package** |               |     |     |
|                    | **dpkg-reconfigure [options] packages**      |               |     |     |
|                    | -r                                           | --remove      |     |     |

## Red Hat

**Package Format**: PACKAGE-NAME-VERSION-RELEASE.ARCHITECTURE.rpm
**ex**: docker-1.13.1-94.gitb2f74b2.el7.centos.x86_64.rpm

| COMMANDS        | OPTIONS                                                         |                                         |     |     |
| --------------- | --------------------------------------------------------------- | --------------------------------------- | --- | --- |
| yumdownloader   | **download RPM packages from Yum repositories**                 |                                         |     |     |
|                 |                                                                 |                                         |     |     |
| rpm             | **RPM Package Manager**                                         |                                         |     |     |
|                 | **q\|--query**                                                  |                                         |     |     |
|                 | -a, --all                                                       |                                         |     |     |
|                 | -p, --package PACKAGE_FILE                                      |                                         |     |     |
|                 | --changelog                                                     |                                         |     |     |
|                 | --i, --info                                                     |                                         |     |     |
|                 | -l, --list                                                      |                                         |     |     |
|                 | -d, --docfiles                                                  |                                         |     |     |
|                 | -c, --configfiles                                               |                                         |     |     |
|                 | -f, --file FILE                                                 |                                         |     |     |
|                 | --provides                                                      | List capabilities this package provides |     |     |
|                 | -R, --requires                                                  |                                         |     |     |
|                 | -s, --state                                                     |                                         |     |     |
|                 | **V\|--verify**                                                 |                                         |     |     |
|                 | **i\|--install**                                                |                                         |     |     |
|                 | **U\|--upgrade**                                                |                                         |     |     |
|                 | **F\|--freshen**                                                |                                         |     |     |
|                 | **e\|--erase**                                                  |                                         |     |     |
| yum             | **Yellowdog Updater Modified**                                  |                                         |     |     |
|                 | **yum [options] command [package ...]**                         |                                         |     |     |
|                 | --downloadonly                                                  |                                         |     |     |
|                 | install                                                         |                                         |     |     |
|                 | reinstall                                                       |                                         |     |     |
|                 | localinstall                                                    |                                         |     |     |
|                 | list                                                            |                                         |     |     |
|                 | upgrade                                                         |                                         |     |     |
|                 | remove                                                          |                                         |     |     |
|                 | autoremove                                                      |                                         |     |     |
|                 | clean all                                                       |                                         |     |     |
|                 | group [...]                                                     |                                         |     |     |
| package-cleanup | **clean up locally installed, duplicate, or orphaned packages** |                                         |     |     |
|                 | --leaves                                                        |                                         |     |     |
|                 |                                                                 |                                         |     |     |
|                 |                                                                 |                                         |     |     |
|                 |                                                                 |                                         |     |     |
|                 |                                                                 |                                         |     |     |

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

| COMMANDS | OPTIONS                                        |     |     |     |
| -------- | ---------------------------------------------- | --- | --- | --- |
| ps       | **report a snapshot of the current processes** |     |     |     |
|          | **ps [options]**                               |     |     |     |
|          | **SIMPLE PROCESS SELECTION**                   |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          | **SIMPLE PROCESS SELECTION**                   |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          | **SIMPLE PROCESS SELECTION**                   |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          | **SIMPLE PROCESS SELECTION**                   |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          | **SIMPLE PROCESS SELECTION**                   |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |
|          |                                                |     |     |     |

```bash
# Process
ps [-e] [-H] [-F] [-f] [-l]
ps -e --format uid,pid,ppid,%cpu --sort [-]%cpu
ps [-U] [-u] [-G] [-g]  root
ps -C firefox
ps -U grant --format %mem | awk '{memory +=$1};END {print memory}'

# Active process
top
$ free -h

# Employing Multiple Screens
$ screen -ls
$ w
# Multiplexing with tmux
$ tmux new
$ tmux ls




# Signal
Number Name    Description
1      HUP     Hangs up
2      INT     Interrupts
3      QUIT    Stops running
9      KILL    Unconditionally terminates
11     SEGV    Segments violation
15     TERM    Terminates if possible
17     STOP    Stops unconditionally, but doesn’t terminate
18     TSTP    Stops or pauses, but continues to run in background
19     CONT    Resumes execution after STOP or TSTP
$ kill -s HUP 2305
$ killall stress-ng
$ pgrep -t tty3
$ sudo pkill -t tty3

pidof crond
pgrep crond
kill -l
kill <pid>
kill -USR1 <pid>
kill -USR1 $(pidof dd)
killall crond
killall -u grant
dd if=/dev/zero of=/dev/null

# Process Niceness/Priority (-19 -> 19, lower best)
nice -n VALUE COMMAND
nice -2 top
sudo nice --2 top
renice 5 <pid>

# Forcegroud/Backgroud
watch ps -C dd --format pid,cmd,%cpu
nohup <command> & # nohup.out
$ jobs
$ jobs -l

bg
fg
$ fg %2
$ bg %2
$ kill %1
$ nohup bash CriticalBackups.sh &


```

```bash
# Shared library
# 1. LD_LIBRARY_PATH environment variable
# 2. Program’s PATH environment variable
# 3. /etc/ld.so.conf.d/ folder
# 4. /etc/ld.so.conf file
# 5. /lib*/ and /usr/lib*/ folders
$ locate ld-linux
$ ldconfig -v 2> /dev/null | grep libmysqlclient
$ ldd /usr/bin/echo

```
