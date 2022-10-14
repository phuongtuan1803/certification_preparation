# LPIC-1: Chapter 4: Managing Files

## ========================= COURSE =======================

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 10 & 11

## ========================= MAIN =========================

```bash
# Globbing
ls /etc/*.conf
ls /etc/?.conf
ls /etc/[-a-zA-Z0-9].conf
ls /etc/[!a-zA-Z0-9].conf
ls {*.jpg,*.gif,*.png}

# similar BRE without ^$ . ()
* [abc][!0-9] 
[:digit/upper/lower/alpha/alnum/space:]
[:graph/print/punct/cntrl/xdigit:]
```

```bash
# Copy file
cp -pf [-v] [-i] [-r] [-a] [-b] [-n] [-u]
# Move and rename
mv [-b] [-f] [-v]
# Remove
rm [-r] [-f] [-i]
rmdir
# Globbing
[cd] {c,d} ? 
+(c|d) # extend 

# Link
ln # hard link
ln -s #symbolic link
stat
```

### Permission and Ownership

```bash
# User
sudo useradd bob
sudo groupadd bob
sudo passwd bob
sudo chage -l bob
sudo userdel -r bob

# Modify
usermod [-d] [-g] [-G] [-a] [-l] [-L] [-U] [-m] [-s]
usermode -a -G audio bob
usermode -s /sbin/nologin bob
passwd [-d] [-e] [-l] [-u] [-E 0] [-E -1] [-S] [-l]

# File attribute ACL (Access control list)
ls -Z a.txt
setfacl -m user:root:rwx a.txt
getfacl -t a.txt
chattr +i a.txt
lsattr a.txt

chown [-r] <user>:<group> file/dir
chmod 777 a.txt
chmode u+a a.txt
umask [-S] # dir default = 777 -umask,  file default = 666 -umask, 
# SUID 4, SGID 2, Sticky 1
```

## ========================= FILES ========================

```bash
/etc/passwd
/etc/shadow # !!: pw have not set, !: user lock
/etc/login.defs
/etc/default/useradd
/etc/skel
```

## ========================= PRACTICE ====================

```bash

```
