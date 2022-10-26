# Basic Linux Command Cheatsheet

## ls

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
## man

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
