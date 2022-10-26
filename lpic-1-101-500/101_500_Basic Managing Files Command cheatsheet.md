# Basic Managing Files Command Cheatsheet

## Basic

| COMMANDS | OPTIONS |                              |                                                                                                           |     |
| -------- | ------- | ---------------------------- | --------------------------------------------------------------------------------------------------------- | --- |
| cp       |         |                              | **cp [OPTION]... [-T] SOURCE DES**                                                                        |     |
|          |         |                              | **cp [OPTION]... SOURCE... DIRECTORY**                                                                    |     |
|          |         |                              | **cp [OPTION]... -t DIRECTORY SOURCE...**                                                                 |     |
|          | -t      | --target-directory=DIRECTORY | copy all SOURCE arguments into DIRECTORY                                                                  |     |
|          | -T      | --no-target-directory        | treat DEST as a normal file                                                                               |     |
|          | -p      |                              | --preserve=mode,ownership,timestamps                                                                      |     |
|          | -f      | --force                      |                                                                                                           |     |
|          | -v      | --verbose                    |                                                                                                           |     |
|          | -i      | --interactive                | prompt                                                                                                    |     |
|          | -r      | --recursive                  |                                                                                                           |     |
|          | -a      | --archive                    |                                                                                                           |     |
|          | -b      |                              | like --backup but does not accept an argument                                                             |     |
|          | -n      | --no-clobber                 | do not overwrite an existing file                                                                         |     |
|          | -u      | --update                     | copy only when the SOURCE file is newer than the destination file or when the destination file is missing |     |
| mv       |         |                              | **mv [OPTION]... [-T] SOURCE DEST**                                                                       |     |
|          |         |                              | **mv [OPTION]... SOURCE... DIRECTORY**                                                                    |     |
|          |         |                              | **mv [OPTION]... -t DIRECTORY SOURCE...**                                                                 |     |
|          | -b      |                              |                                                                                                           |     |
|          | -f      |                              |                                                                                                           |     |
|          | -i      |                              |                                                                                                           |     |
|          | -i      |                              |                                                                                                           |     |
|          | -n      |                              |                                                                                                           |     |
| rm       |         |                              | **rm [OPTION]... [FILE]...**                                                                              |     |
|          | -r      | --recursive                  |                                                                                                           |     |
|          | -f      | --force                      |                                                                                                           |     |
|          | -i      |                              | prompt before every removal                                                                               |     |
|          | -I      |                              | prompt once before removing more than three files, or when removing recursively                           |     |
|          | -d      | --dir                        | remove empty directories                                                                                  |     |
| rmdir    |         |                              | **rmdir [OPTION]... DIRECTORY...**                                                                        |     |
|          |         |                              | Remove the DIRECTORY(ies), if they are empty                                                              |     |
| ln       |         |                              | **ln [OPTION]... [-T] TARGET LINK_NAME**                                                                  |     |
|          |         |                              | **ln [OPTION]... TARGET**                                                                                 |     |
|          |         |                              | **ln [OPTION]... TARGET... DIRECTORY**                                                                    |     |
|          |         |                              | **ln [OPTION]... -t DIRECTORY TARGET...**                                                                 |     |
|          | -s      | --symbolic                   |                                                                                                           |     |
| stat     |         |                              | **stat [OPTION]... FILE...**                                                                              |     |
|          | -L      |                              |                                                                                                           |     |
|          | -f      |                              |                                                                                                           |     |
|          | -c      | --format=FORMAT              |                                                                                                           |     |
|          |         | --printf=FORMAT              | like --format, but interpret backslash escapes                                                            |     |
|          | -t      | --terse                      | print the information in terse form                                                                       |     |
|          | -f      |                              |                                                                                                           |     |

Note: # Globbing
[cd] {c,d} ? +(c|d) # extend 

## Compressed

| COMMANDS              | OPTIONS                                                 |     |     |                    |
| --------------------- | ------------------------------------------------------- | --- | --- | ------------------ |
| gzip, gunzip, zcat    | **gzip [ -acdfhlLnNrtvV19 ] [-S suffix] [ name ...  ]** |     |     |                    |
|                       | **gunzip [ -acfhlLnNrtvV ] [-S suffix] [ name ...  ]**  |     |     |                    |
|                       | **zcat [ -fhLV ] [ name ...  ]**                        |     |     |                    |
|                       | -                                                       |     |     |                    |
| bzip2, bunzip2, bzcat | **bzip2 [ -cdfkqstvzVL123456789 ] [ filenames ...  ]**  |     |     |                    |
|                       | **bunzip2 [ -fkvsVL ] [ filenames ...  ]**              |     |     |                    |
|                       | **bzcat [ -s ] [ filenames ...  ]**                     |     |     |                    |
|                       | -                                                       |     |     |                    |
| xz, unxz, xzcat       | **xz [option...]  [file...]**                           |     |     |                    |
|                       | -                                                       |     |     |                    |
| zip                   |                                                         |     |     | zip -r foo.zip foo |
|                       | -                                                       |     |     |                    |
## Archiving

| COMMANDS | OPTIONS                                          |                         |                                                                 |                                                    |
| -------- | ------------------------------------------------ | ----------------------- | --------------------------------------------------------------- | -------------------------------------------------- |
| cpio     | **copy files to and from archives**              |                         |                                                                 |                                                    |
|          | -i                                               | --extract               |                                                                 | cpio -itvI Project4x.cpio                          |
|          | -t                                               | --list                  |                                                                 | cpio -iv --no-absolute-filenames -I Project4x.cpio |
|          | -v                                               | --verbose               |                                                                 |                                                    |
|          | -I                                               |                         | Use ARCHIVE-NAME instead of standard input                      |                                                    |
|          |                                                  | --no-absolute-filenames | Create all files relative to the current directory.             |                                                    |
| dd       | **convert and copy a file**                      |                         |                                                                 |                                                    |
|          | if=FILE                                          |                         | read from FILE instead of stdin                                 | dd if=/dev/sdb of=/dev/sdc status=progress         |
|          | of=FILE                                          |                         | write to FILE instead of stdout                                 |
| tar      | **The GNU version of the tar archiving utility** |                         |                                                                 |                                                    |
|          |                                                  |                         |                                                                 | tar -cvf Project4x.tar Project4?.txt               |
|          | -c                                               |                         | create a archive file.                                          |
|          | -x                                               |                         | extract a archive file.                                         |
|          | -v                                               |                         | show the progress of archive file.                              |
|          | -f                                               |                         | filename of archive file.                                       |
|          | -t                                               |                         | viewing content of archive file.                                |
|          | -j                                               | --bzip2                 | filter archive through bzip2.                                   |
|          | -J                                               | --xz                    | filter archive through bzip2.                                   |
|          | -z                                               | --gzip                  | filter archive through gzip.                                    |
|          | -r                                               |                         | append or update files or directories to existing archive file. |
|          | -W                                               |                         | Verify a archive file.                                          |


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
chmod u+a a.txt
umask [-S] # dir default = 777 -umask,  file default = 666 -umask, 
# SUID 4, SGID 2, Sticky 1
```
