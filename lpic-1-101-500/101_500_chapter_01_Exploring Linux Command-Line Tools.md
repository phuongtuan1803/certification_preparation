# LPIC-1: Chapter 1: Exploring Linux Command-Line Tools

## ========================= COURSE =======================

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 7 & 9

## ========================= MAIN =========================

```bash
mkdir newdir && cd newdir || echo "create dir failed!"
{ echo Hello ; echo Hi; } > tmp

a=0; ( a=10; echo in=$a; ) ; echo out=$a
a=0; { a=10; echo in=$a; } ; echo out=$a

grep tcp /ect/service | awk '{print $1}' | sort | less
```


## Text Filters

```bash
               
pr     fmt     expand     
awk
paste     tr     bzcat     xzcat     zcat

# File-Combining Commands
cat
# File-Transforming Commands
od [-c] [-b] filename
split/join
# File-Formatting Commands
sort
nl
# File-Viewing Commands
more
less
tail/head [-f]  
# File-Summarizing Commands
wc
cut
uniq
File-Summarizing Commands
md5sum/sha256sum/sha512sum
# Using Streams, Redirection, and Pipes
sed
# Generating Command Lines
xargs
ls -1 EmptyFile?.txt | xargs -p /usr/bin/rm
rm -i $(ls EmptyFile?.txt)

```

## Edit Text

```bash
sed -n '/^root/p' passwd
sed -n 's/^root/tuan/p' passwd
```

## Find text

```bash
locate [-c] [-A] [-i] [--regexp or --regex] *.png
locate -S
sudo updatedb

find / [-user usr_name] [-group gr_name] [-name *bzip2*] [-size +1M] [-mtime -1]
find / [-type f]
find / [-exec stat -c "%s %n" {} \;]

grep [-i] [-v] [-c] [-o] [-r] [-w] [-f filename] [-q] [-x] [-E]
```


## ========================= FILES ========================

```bash
/etc/profile
/etc/profile.d
~/.bash_profile
~/.bashrc (run /etc/bashrc)
/etc/bashrc
```

## ========================= PRACTICE ====================

```bash
less
emacs/nano/vim
```
