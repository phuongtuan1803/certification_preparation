# LPIC-1: Chapter 2: Managing Software and Processes

## ========================= COURSE =======================

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 4 & 5 & 8

## ========================= MAIN =========================

```bash
# Debian
# PACKAGE-NAME-VERSION-RELEASE_ARCHITECTURE.deb
# ex: docker_1.5-1build1_amd64.deb

dpkg [--info] [-c] [-L] [-i] [-S] <package>
dpkg [-c] [-r] <package>
apt-cache
apt-cdrom
apt-config
atp-get [download]
apt-key
apt info
apt search
apt show
apt list
apt remove
apt autoremove
apt purge
apt full-upgrade

# repository
# - main
# - universer
# - restricted
# - multiverse
apt policy
add-apt-repository 'respository'
add-apt-repository --remove 'respository'

sudo dpkg-reconfigure cups

```

```bash
# Red Hat
# PACKAGE-NAME-VERSION-RELEASE.ARCHITECTURE.rpm
# ex: docker-1.13.1-94.gitb2f74b2.el7.centos.x86_64.rpm
yumdownloader emacs
rpm2cpio emacs-24.3-22.el7.x86_64.rpm > emacs.cpio
cpio -idv < emacs.cpio

rpm [-qa] [-qi] [Group="System Environment/Shells"] [-ql yum] [-qd yum] [-qc yum] [-qf /bin/bash] [-q --provides bash]
rpm [-q --requires bash] [-q --changelog bash]
rpm [-qip] [-qlp] a.rpm
rpm ACTION [OPTION] PACKAGE-FILE
rmp [-e] [-F] [-i] [-q] [-U] [-V]
yum install -y yum-plugin-downloadonly
yum install -y --downloadonly --downloaddir=/tmp/packages

yum install tree
yum localinstall a.rmp
yum reinstall [--skip-broken] tree
yum localinstall a.rmp
yum list updates
yum upgrade
yum remove tree
yum autoremove tree
package-cleanup [--leaves]

yum group list ids
yum group install "Security Tools" [--setopt=group_package_types=mandatory,default,optional]
yum group install security-tools
yum install @"Security Tools"
yum install @security-tools

yum group [remove/autoremove] security-tools
yum group update security-tools
yum group info security-tools
```

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

## ========================= FILES ========================

```bash
/etc/apt/sources.list
/etc/apt/sources.list.d/*
/etc/yum.conf
```

## ========================= PRACTICE ====================

```bash

```
