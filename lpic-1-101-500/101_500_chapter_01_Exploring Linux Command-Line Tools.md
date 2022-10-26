# LPIC-1: Chapter 1: Exploring Linux Command-Line Tools

## ========================= COURSE =======================

***Cert Prep: LPIC-1 Exam 101 (Version 5.0)*** : Part 7 & 9

## ========================= MAIN =========================

```bash
mkdir newdir && cd newdir || echo "create dir failed!"
{ echo Hello ; echo Hi; } > tmp

a=0; ( a=10; echo in=$a; ) ; echo out=$a
a=0; { a=10; echo in=$a; } ; echo out=$a

pwd
readlink /bin/sh
uname [-r] [-a]
type [echo/uname]
man [-k] [-S 5] passwd

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

```bash
# Environment Variables
Name Description
BASH_VERSION       - Current Bash shell instance’s version number (Chapter 1)
EDITOR             - Default editor used by some shell commands (Chapter 1)
GROUPS             - User account’s group memberships (Chapter 7)
HISTFILE           - Name of the user’s shell command history file (Chapter 1)
HISTSIZE           - Maximum number of commands stored in history file (Chapter 1)
HOME               - Current user’s home directory name (Chapter 1)
HOSTNAME           - Current system’s host name (Chapter 8)
LANG               - Locale category for the shell (Chapter 6)
LC_*               - Various locale settings that override LANG (Chapter 6)
LC_ALL             - Locale category for the shell that overrides LANG (Chapter 6)
LD_LIBRARY_PATH    - Colon-separated list of library directories to search prior to looking through the standard library directories  Chapter 2)
PATH               - Colon-separated list of directories to search for commands (Chapter 1)
PS1                - Primary shell command-line interface prompt string (Chapter 1)
PS2                - Secondary shell command-line interface prompt string
PWD                - User account’s current working directory (Chapter 1)
SHLVL              - Current shell level (Chapter 1)
TZ                 - User’s time zone, if different from system’s time zone (Chapter 6)
UID                - User account’s user identification number (Chapter 7)
VISUAL             - Default screen-based editor used by some shell commands (Chapter 1)
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
