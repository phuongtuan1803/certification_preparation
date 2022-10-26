# Basic Linux Command Cheatsheet

## ls

| OPTIONS |                    |                                    |                                                         |   |
|---------|--------------------|------------------------------------|---------------------------------------------------------|---|
|         | -a<br>-A           | --all<br>--almost-all              | <br>without . and ..                                    |   |
|         | -B                 | --ignore-backups                   | file start with ~                                       |   |
|         | <br>-f<br>-c<br>-S | --sort=WORD                        |                                                         |   |
|         | -d                 | --directory                        | list dir themselves                                     |   |
|         | -F                 | --classify                         | append indicator (one of */=>@\|)                       |   |
|         | -r                 | --reverse                          | reverse order while sorting                             |   |
|         | -R                 | --recursive                        |                                                         |   |
|         | -s<br>-S           | --size                             | <br>sort by file size                                   |   |
|         | -l<br>-g<br>-G     | <br><br>--no-group                 | long listing format<br>not list owner<br>not list group |   |
|         | -h                 | --human-readable                   |                                                         |   |
|         | -H                 | --dereference-command-line         | symbolic links listed                                   |   |
|         | -i                 | --inode                            |                                                         |   |
|         | -I                 | --ignore=PATTERN<br>--hide=PATTERN |                                                         |   |
|         | -n                 | --numeric-uid-gid                  |                                                         |   |
|         | -1                 |                                    | one file per line                                       |   |
|         |                    |                                    |                                                         |   |
|         |                    |                                    |                                                         |   |
|         |                    |                                    |                                                         |   |

## grep

SYNOPSIS

```bash
       grep [OPTIONS] PATTERN [FILE...]
       grep [OPTIONS] [-e PATTERN | -f FILE] [FILE...]
```

| OPTIONS                      |              |                                                                              |                                                     | example |
|------------------------------|--------------|------------------------------------------------------------------------------|-----------------------------------------------------|---------|
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

| OPTIONS |    |                                                                                      |
|---------|----|--------------------------------------------------------------------------------------|
|         | -k | Search the short descriptions and manual page names                                  |
|         | -f | Lookup the manual pages referenced and print out the short descriptions of any found |
