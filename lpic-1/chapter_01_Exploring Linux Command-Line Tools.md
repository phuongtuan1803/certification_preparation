# LPIC-1: Chapter 1: Exploring Linux Command-Line Tools

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 7 & 9

## ========================= Main =========================

```bash
mkdir newdir && cd newdir || echo "create dir failed!"
{ echo Hello ; echo Hi; } > tmp

a=0; ( a=10; echo in=$a; ) ; echo out=$a
a=0; { a=10; echo in=$a; } ; echo out=$a

prinenv | grep A
printenv A
set -o posix
set +o posix
export A
export -n A
unset A

history
ls /etc
!ls
cd !*
!!
ctrl +A

which
whereis

grep tcp /ect/service | awk '{print $1}' | sort | less
```

## Named pipe

```bash
mkfifo named_pipe
echo "Hi" > named_pipe
cat named_pipe
\>     >>     2>     2>>     &>     &>>
< >     tee [-a]
/dev/null
```

## Text Filters

```bash
sed     cat     less     head/tail [-f]     wc     sort     uniq     split/join
nl     pr     fmt     expand     cut
awk
od     paste     tr     md5sum     sha256sum     sha512sum     bzcat     xzcat     zcat
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

## Regex

```bash
# BRE
^$ .* [abc][!0-9] [:digit/upper/lower/alpha/alnum/space:]
[:graph/print/punct/cntrl/xdigit:] ()
```

```bash
# ERE
. [] \ () | *+{} ?
^$ [^abc]
\b \B \< \> \w \W \s \S
. .? .+ .* .{3} .{3,} .{,3} .{1,3}
^(dog|cat)?$
Backreference:
(ss).*\1
```

## ========================= Files =========================

```bash
/etc/profile
/etc/profile.d
~/.bash_profile
~/.bashrc (run /etc/bashrc)
/etc/bashrc
```

## ========================= More Practice =================

```bash
less
vim
```