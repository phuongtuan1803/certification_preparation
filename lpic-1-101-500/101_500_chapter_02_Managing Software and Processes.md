# LPIC-1: Chapter 2: Managing Software and Processes

## ========================= COURSE =======================

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 4 & 5 & 8

## ========================= MAIN =========================

```bash
# Debian
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
```

```bash
# Red Hat
rpm [-qa] [-qi] [Group="System Environment/Shells"] [-ql yum] [-qd yum] [-qc yum] [-qf /bin/bash] [-q --provides bash]
rpm [-q --requires bash] [-q --changelog bash]
rpm [-qip] [-qlp] a.rpm

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

# Signal
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
nice -2 top
sudo nice --2 top
renice 5 <pid>

# Forcegroud/Backgroud
watch ps -C dd --format pid,cmd,%cpu
nohup <command> & # nohup.out
jobs
bg
fg

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
