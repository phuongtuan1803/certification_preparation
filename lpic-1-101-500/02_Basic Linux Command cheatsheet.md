# Basic Linux Command Cheatsheet

## Basic

```bash
# && execute if previous command done
# || execute if previous command faile
mkdir newdir && cd newdir || echo "create dir failed!" 

# (variable scope)
# {there are no differences}
a=0; ( a=10; echo in=$a; ) ; echo out=$a
a=0; { a=10; echo in=$a; } ; echo out=$a
```

## ls

| OPTIONS |                    | **ls [OPTION]... [FILE]...**       |                                                         |     |
| ------- | ------------------ | ---------------------------------- | ------------------------------------------------------- | --- |
|         | -a<br>-A           | --all<br>--almost-all              | <br>without . and ..                                    |     |
|         | -B                 | --ignore-backups                   | file start with ~                                       |     |
|         | <br>-f<br>-c<br>-S | --sort=WORD                        |                                                         |     |
|         | -d                 | --directory                        | list dir themselves                                     |     |
|         | -F                 | --classify                         | append indicator (one of */=>@\|)                       |     |
|         | -r                 | --reverse                          | reverse order while sorting                             |     |
|         | -R                 | --recursive                        |                                                         |     |
|         | -s<br>-S           | --size                             | <br>sort by file size                                   |     |
|         | -l<br>-g<br>-G     | <br><br>--no-group                 | long listing format<br>not list owner<br>not list group |     |
|         | -h                 | --human-readable                   |                                                         |     |
|         | -H                 | --dereference-command-line         | symbolic links listed                                   |     |
|         | -i                 | --inode                            |                                                         |     |
|         | -I                 | --ignore=PATTERN<br>--hide=PATTERN |                                                         |     |
|         | -n                 | --numeric-uid-gid                  |                                                         |     |
|         | -1                 |                                    | one file per line                                       |     |

Note:similar BRE without ^$ . ()
example: ls {*.jpg,*.gif,*.png}

## Find

| COMMANDS | OPTIONS          |               |                                                                                                |                                      |
| -------- | ---------------- | ------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------ |
| locate   |                  |               | **locate [OPTION]... PATTERN...**                                                              |                                      |
|          |                  |               | **sudo updatedb** # update database                                                            |                                      |
|          | -c               | --count       |                                                                                                |                                      |
|          | -A               | --all         | Print only names which match all non-option arguments                                          |                                      |
|          | -i               | --ignore-case |                                                                                                |                                      |
|          | -r               | --regexp      | basic regex                                                                                    |                                      |
|          |                  | --regex       | extend regex                                                                                   |                                      |
|          |                  |               |                                                                                                |                                      |
| find     |                  |               | **find [-H] [-L] [-P] [-D debugopts] [-Olevel] [path...] [expression]**                        |                                      |
|          | -P               |               | Never  follow  symbolic  links                                                                 |                                      |
|          | -L               |               | Follow symbolic links.                                                                         |                                      |
|          | -H               |               | Do not follow symbolic links, except while processing the command line arguments               |                                      |
|          | -D debugoptions  |               |                                                                                                |                                      |
|          | -Olevel          |               |                                                                                                |                                      |
|          | -maxdepth levels |               |                                                                                                |                                      |
|          | -mindepth levels |               |                                                                                                |                                      |
|          | -type c          |               | b(block (buffered) special), c(character (unbuffered) special), d(directory), f(regular files) |                                      |
|          | -name pattern    | n             |                                                                                                |                                      |
|          | -size xxx        |               | +1M                                                                                            |                                      |
|          | -user uname      |               |                                                                                                |                                      |
|          | -group gname     |               |                                                                                                |                                      |
|          | -perm mode       |               |                                                                                                |                                      |
|          | -regex pattern   |               |                                                                                                |                                      |
|          | -exec command ;  |               |                                                                                                | find / [-exec stat -c "%s %n" {} \;] |

## grep

SYNOPSIS

```bash
       grep [OPTIONS] PATTERN [FILE...]
       grep [OPTIONS] [-e PATTERN | -f FILE] [FILE...]
```

| OPTIONS                      |              |                                                                              |                                                     | example |
| ---------------------------- | ------------ | ---------------------------------------------------------------------------- | --------------------------------------------------- | ------- |
| Information                  | -            | -                                                                            | -                                                   |         |
| Matcher Selection            | -E           | --extended-regexp                                                            |                                                     |         |
|                              | -G           | --basic-regexp                                                               |                                                     |         |
| Matching Control             | -e PATTERN   | --regexp=PATTERN                                                             | pattern form PATTERN                                |         |
|                              | -f FILE      | --file=FILE                                                                  | pattern from FILE                                   |         |
|                              | -i           | --ignore-case                                                                |                                                     |         |
|                              | -v           | --invert-match                                                               | invert match                                        |         |
|                              | -w           | --word-regexp                                                                | whole word match                                    |         |
|                              | -x           | --line-regexp                                                                | whole line match                                    |         |
| Output Control               | -c           | --count                                                                      |                                                     |         |
|                              |              | --color                                                                      |                                                     |         |
|                              | -L<br>-l     | --files-without-match<br>--files-with-match                                  |                                                     |         |
|                              | -o           | --only-matching                                                              |                                                     |         |
|                              | -q<br><br>-s | --quite<br>--silent<br>--no-messages                                         |                                                     |         |
| Prefix Control               | -b           | --byte-offset                                                                |                                                     |         |
|                              | -H<br>-h     | --with-filename<br>--no-filename                                             |                                                     |         |
|                              | -n           | --line-number                                                                |                                                     |         |
| Context Line Control         | -            | -                                                                            | -                                                   |         |
| File and Directory Selection | -a<br>-I     | --text                                                                       | --binary-files=text<br>--binary-files=without-match |         |
|                              |              | --exclude=GLOB<br>--exclude-from=FILE<br>--exclude-dir=DIR<br>--include=GLOB |                                                     |         |
|                              | -r<br>-R     | --recursive<br>--dereference-recursive                                       | <br>follow all symbolic links                       |         |

## Regex

```bash
# BRE
^$ .* [abc][!0-9]
[:digit/upper/lower/alpha/alnum/space:]
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

## man

The section numbers of the manual followed by the types of pages they contain.

1. Executable programs or shell commands
2. System calls (functions provided by the kernel)
3. Library calls (functions within program libraries)
4. Special files (usually found in /dev)
5. File formats and conventions eg /etc/passwd
6. Games
7. Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
8. System administration commands (usually only for root)
9. Kernel routines [Non standard]

| OPTIONS |     |                                                                                      |
| ------- | --- | ------------------------------------------------------------------------------------ |
|         | -k  | Search the short descriptions and manual page names                                  |
|         | -f  | Lookup the manual pages referenced and print out the short descriptions of any found |
|         | -S  | man -S 5 passwd # section 5                                                          |

## Text Filters

|                                 | command                    | param | description                                         | example                                                    |
| ------------------------------- | -------------------------- | ----- | --------------------------------------------------- | ---------------------------------------------------------- |
| File-Combining Commands         | cat                        |       | concatenate files and print on the standard output  |                                                            |
| File-Transforming Commands      | od [-c] [-b] filename      |       | dump files in octal and other formats               |                                                            |
|                                 | split                      |       | split a file into pieces                            |                                                            |
|                                 | join                       |       | join lines of two files on a common field           |                                                            |
| File-Formatting Commands        | sort                       |       | sort lines of text files                            |                                                            |
|                                 | nl                         |       | number lines of files                               |                                                            |
| File-Viewing Commands           | more/less                  |       |                                                     |                                                            |
|                                 | tail/head [-f]             |       |                                                     |                                                            |
| File-Summarizing Commands       | wc                         |       | print newline, word, and byte counts for each file  |                                                            |
|                                 | cut                        |       | remove sections from each line of files             |                                                            |
|                                 | uniq                       |       | report or omit repeated lines                       |                                                            |
| Streams, Redirection, and Pipes | sed                        |       | stream editor for filtering and transforming text   | sed -n '/^root/p' passwd<br>sed -n 's/^root/tuan/p' passwd |
| Misc                            | md5sum/sha256sum/sha512sum |       | compute and check                                   |                                                            |
|                                 | xargs                      |       | build and execute command lines from standard input |                                                            |
|                                 | pr                         |       | convert text files for printing                     |                                                            |
|                                 | fmt                        |       | simple optimal text formatter                       |                                                            |
|                                 | expand                     |       | convert tabs to spaces                              |                                                            |
|                                 | awk                        |       | pattern scanning and processing language            |                                                            |
|                                 | paste                      |       | merge lines of files                                |                                                            |
|                                 | tr                         |       | translate or delete characters                      |                                                            |
|                                 | bzcat/xzcat/zcat           |       | decompresses files to stdout                        |                                                            |
|                                 |                            |       |                                                     |                                                            |

## History

| COMMAND |         |                                  |
| ------- | ------- | -------------------------------- |
|         | history | display the command history list |
|         | !ls     | run last ls command              |
|         | cd !*   | run with last param              |
|         | !!      | run last command                 |

## Named pipe

| COMMAND                   |                                                                                  |
| ------------------------- | -------------------------------------------------------------------------------- |
| >                         | stout to file                                                                    |
| >>                        | append stout to file                                                             |
| 2>                        | sterr to file                                                                    |
| 2>>                       | append sterr to file                                                             |
| &>                        | stout and sterr to file                                                          |
| &>>                       | append stdout and sterr to file                                                  |
| < A > B                   | read from A and write to B                                                       |
| > /dev/null               | ignore                                                                           |
| tee [OPTION]... [FILE]... | read from standard input and write to standard output and files <br>-a, --append |
|                           |                                                                                  |

## Environment Variables

| Name            | Description                                                                                                                 |
| --------------- | --------------------------------------------------------------------------------------------------------------------------- |
| BASH_VERSION    | Current Bash shell instance’s version number (Chapter 1)                                                                    |
| EDITOR          | Default editor used by some shell commands (Chapter 1)                                                                      |
| GROUPS          | User account’s group memberships (Chapter 7)                                                                                |
| HISTFILE        | Name of the user’s shell command history file (Chapter 1)                                                                   |
| HISTSIZE        | Maximum number of commands stored in history file (Chapter 1)                                                               |
| HOME            | Current user’s home directory name (Chapter 1)                                                                              |
| HOSTNAME        | Current system’s host name (Chapter 8)                                                                                      |
| LANG            | Locale category for the shell (Chapter 6)                                                                                   |
| LC_*            | Various locale settings that override LANG (Chapter 6)                                                                      |
| LC_ALL          | Locale category for the shell that overrides LANG (Chapter 6)                                                               |
| LD_LIBRARY_PATH | Colon-separated list of library directories to search prior to looking through the standard library directories  Chapter 2) |
| PATH            | Colon-separated list of directories to search for commands (Chapter 1)                                                      |
| PS1             | Primary shell command-line interface prompt string (Chapter 1)                                                              |
| PS2             | Secondary shell command-line interface prompt string                                                                        |
| PWD             | User account’s current working directory (Chapter 1)                                                                        |
| SHLVL           | Current shell level (Chapter 1)                                                                                             |
| TZ              | User’s time zone, if different from system’s time zone (Chapter 6)                                                          |
| UID             | User account’s user identification number (Chapter 7)                                                                       |
| VISUAL          | Default screen-based editor used by some shell commands (Chapter 1)                                                         |

## Misc

### misc command

| COMMAND |           |                                                                          |
| ------- | --------- | ------------------------------------------------------------------------ |
|         | which     | shows the full path of (shell) commands                                  |
|         | whereis   | Locate the binary, source, and manual page files for a command           |
|         | whatis    | display manual page descriptions                                         |
|         | mkfifo    | make FIFOs (named pipes)                                                 |
|         | readlink  | print resolved symbolic links or canonical file names                    |
|         | type      | print type of files                                                      |
|         | uname     | [-r] [-a]                                                                |
|         | pwd       | print name of current/working directory                                  |
|         | prinenv   | print environment variables                                              |
|         | set/unset | set/unset shell variable <br>set -o posix, not shown function            |
|         | export    | -p    exported variables on current shell<br>-f    export with functions |
|         |           |                                                                          |
|         |           |                                                                          |

<!-- TODO: Text filter -->