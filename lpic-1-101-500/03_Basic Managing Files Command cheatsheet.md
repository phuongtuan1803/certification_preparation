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
|          | of=FILE                                          |                         | write to FILE instead of stdout                                 |                                                    |
| tar      | **The GNU version of the tar archiving utility** |                         |                                                                 |                                                    |
|          |                                                  |                         |                                                                 | tar -cvf Project4x.tar Project4?.txt               |
|          | -c                                               |                         | create a archive file.                                          |                                                    |
|          | -x                                               |                         | extract a archive file.                                         |                                                    |
|          | -v                                               |                         | show the progress of archive file.                              |                                                    |
|          | -f                                               |                         | filename of archive file.                                       |                                                    |
|          | -t                                               |                         | viewing content of archive file.                                |                                                    |
|          | -j                                               | --bzip2                 | filter archive through bzip2.                                   |                                                    |
|          | -J                                               | --xz                    | filter archive through bzip2.                                   |                                                    |
|          | -z                                               | --gzip                  | filter archive through gzip.                                    |                                                    |
|          | -r                                               |                         | append or update files or directories to existing archive file. |                                                    |
|          | -W                                               |                         | Verify a archive file.                                          |                                                    |


## Permission and Ownership

| COMMANDS | OPTIONS                                                                   |                                        |                                                                              |                     |
| -------- | ------------------------------------------------------------------------- | -------------------------------------- | ---------------------------------------------------------------------------- | ------------------- |
| useradd  | **useradd [options] LOGIN**                                               |                                        |                                                                              |                     |
|          | **useradd -D**                                                            |                                        |                                                                              |                     |
|          | **useradd -D [options]**                                                  |                                        |                                                                              |                     |
|          | -D                                                                        | --defaults                             |                                                                              |                     |
|          | -d                                                                        | --home-dir HOME_DIR                    |                                                                              |                     |
|          | -e                                                                        | --expiredate EXPIRE_DATE               |                                                                              |                     |
|          | -b                                                                        | --base-dir BASE_DIR                    |                                                                              |                     |
|          | -f                                                                        | --inactive INACTIVE                    |                                                                              |                     |
|          | -N                                                                        | --no-user-group                        |                                                                              |                     |
|          | -g                                                                        | --gid GROUP                            |                                                                              |                     |
|          | -G                                                                        | --groups GROUP1[,GROUP2,...[,GROUPN]]] |                                                                              |                     |
|          | -k                                                                        | --skel SKEL_DIR                        |                                                                              |                     |
|          | -m                                                                        | --create-home                          |                                                                              |                     |
|          | -M                                                                        | --no-create-home                       |                                                                              |                     |
|          | -p                                                                        | --password PASSWORD                    |                                                                              |                     |
| groupadd | **groupadd [options] group**                                              |                                        |                                                                              |                     |
|          | -p                                                                        | --password PASSWORD                    |                                                                              |                     |
|          | -r                                                                        | --system                               | Create a system group                                                        |                     |
|          | -f                                                                        | --force                                | exit with success status if the specified group already exists               |                     |
|          | -K                                                                        | --key KEY=VALUE                        | -K GID_MIN=100  -K GID_MAX=499                                               |                     |
| passwd   | **passwd [options] [LOGIN]**                                              |                                        |                                                                              |                     |
|          | -S                                                                        | --status                               |                                                                              |                     |
|          | -a                                                                        | --all                                  | use with -S                                                                  |                     |
|          | -d                                                                        | --delete                               |                                                                              |                     |
|          | -e                                                                        | --expire                               |                                                                              |                     |
|          | -i                                                                        | --inactive                             |                                                                              |                     |
|          | -w                                                                        | --warndays WARNDAYS                    |                                                                              |                     |
|          | -l                                                                        | --lock                                 |                                                                              |                     |
|          | -u                                                                        | --unlock                               |                                                                              |                     |
|          | -n                                                                        | --mindays MIN_DAYS                     |                                                                              |                     |
|          | -x                                                                        | --maxdays MAX_DAYS                     |                                                                              |                     |
|          | -q                                                                        | --quite                                |                                                                              |                     |
|          |                                                                           |                                        |                                                                              |                     |
| chage    | **change user password expiry information**                               |                                        |                                                                              |                     |
|          | **chage [options] LOGIN**                                                 |                                        |                                                                              |                     |
|          | -d                                                                        | --lastday LAST_DAY                     |                                                                              |                     |
|          | -E                                                                        | --expiredate EXPIRE_DATE               | 1 as the EXPIRE_DATE will remove an account expiration date                  |                     |
|          | -I                                                                        | --inactive INACTIVE                    |                                                                              |                     |
|          | -l                                                                        | --list                                 | Show account aging information.                                              |                     |
|          | -m                                                                        | --mindays MIN_DAYS                     |                                                                              |                     |
|          | -M                                                                        | --maxdays MAX_DAYS                     |                                                                              |                     |
|          | -W                                                                        | --warndays WARN_DAYS                   |                                                                              |                     |
| userdel  | **delete a user account and related files**                               |                                        |                                                                              |                     |
|          | **userdel [options] LOGIN**                                               |                                        |                                                                              |                     |
|          | -f                                                                        | --force                                |                                                                              |                     |
|          | -r                                                                        | --remove                               | Files in the user's home directory + home directory + the user's mail spool. |                     |
| usermod  | **modify a user account**                                                 |                                        |                                                                              |                     |
|          | **usermod [options] LOGIN**                                               |                                        |                                                                              |                     |
|          | -a                                                                        |                                        | Add the user to the supplementary group(s) <br> user with -G                 |                     |
|          | -G                                                                        | --groups GROUP1[,GROUP2,...[,GROUPN]]] |                                                                              |                     |
|          | -g                                                                        | --gid GROUP                            | The group name or number of the user's new initial login group               |                     |
|          | -d                                                                        | --home HOME_DIR                        |                                                                              |                     |
|          | -m                                                                        | --move-home                            |                                                                              |                     |
|          | -e                                                                        | --expiredate EXPIRE_DATE               |                                                                              |                     |
|          | -f                                                                        | --inactive INACTIVE                    |                                                                              |                     |
|          | -l                                                                        | --login NEW_LOGIN                      |                                                                              |                     |
|          | -L                                                                        | --lock                                 |                                                                              |                     |
|          | -U                                                                        | --unlock                               |                                                                              |                     |
|          | -p                                                                        | --password                             |                                                                              |                     |
|          | -s                                                                        | --shell                                | -s /sbin/nologin                                                             |                     |
| chown    | **change file owner and group**                                           |                                        |                                                                              |                     |
|          | **chown [OPTION]... [OWNER][:[GROUP]] FILE...**                           |                                        |                                                                              |                     |
|          | **chown [OPTION]... --reference=RFILE FILE...**                           |                                        |                                                                              |                     |
|          | -c                                                                        | --changes                              |                                                                              |                     |
|          | -f                                                                        | --slient, --quite                      |                                                                              |                     |
|          | -v                                                                        | --verbose                              |                                                                              |                     |
|          | -R                                                                        | --recursive                            |                                                                              | chown root:staff /u |
|          |                                                                           |                                        |                                                                              |                     |
| chmod    | **change file mode bits**                                                 |                                        |                                                                              |                     |
|          | **chmod [OPTION]... MODE[,MODE]... FILE...**                              |                                        |                                                                              |                     |
|          | **chmod [OPTION]... OCTAL-MODE FILE...**                                  |                                        |                                                                              |                     |
|          | **chmod [OPTION]... --reference=RFILE FILE...**                           |                                        |                                                                              |                     |
| umask    | **set file mode creation mask**                                           |                                        |                                                                              |                     |
|          | -S                                                                        |                                        | show detail                                                                  |                     |
| setfacl  | **set file access control lists**                                         |                                        |                                                                              |                     |
|          | **`setfacl [-bkndRLPvh] [{-m|-x} acl_spec] [{-M|-X} acl_file] file ...**` |                                        |                                                                              |                     |
|          | **`setfacl --restore={file|-}**`                                          |                                        |                                                                              |                     |
|          | ex: setfacl -m u:lisa:r file                                                                          |                                        |                                                                              |                     |
|          | ex: setfacl -m m::rx file                                                                          |                                        |                                                                              |                     |
|          | ex: setfacl -x g:staff file                                                                          |                                        |                                                                              |                     |
|          | ex: getfacl file1 | setfacl --set-file=- file2                                                                          |                                        |                                                                              |                     |
|          | ex: getfacl --access dir | setfacl -d -M- dir                                                                          |                                        |                                                                              |                     |
|          |                                                                           |                                        |                                                                              |                     |
|          | -m                                                                        | --modify                               |                                                                              |                     |
|          | -M                                                                        | --modify-file                          |                                                                              |                     |
|          | -x                                                                        | --remove                               |                                                                              |                     |
|          | -X                                                                        | --remove-file                          |                                                                              |                     |
| getfacl  | **get file access control lists**                                         |                                        |                                                                              |                     |
|          | **getfacl [-aceEsRLPtpndvh] file ...**                                    |                                        |                                                                              |                     |
|          | **getfacl [-aceEsRLPtpndvh] -**                                           |                                        |                                                                              |                     |
|          |                                                                           |                                        |                                                                              |                     |
|          |                                                                           |                                        |                                                                              |                     |
| chattr   | **change file attributes on a Linux file system**                         |                                        |                                                                              |                     |
|          | **chattr [ -RVf ] [ -v version ] [ -p project ] [ mode ] files...**       |                                        |                                                                              |                     |
|          | -R                                                                        |                                        | Recursively                                                                  |                     |
|          | -V                                                                        |                                        | Suppress most error messages.                                                |                     |
|          | -f                                                                        |                                        | Suppress most error messages                                                 |                     |
|          |                                                                           |                                        |                                                                              |                     |
| lsattr   | **list file attributes on a Linux second extended file system**           |                                        |                                                                              |                     |
|          | **lsattr [ -RVadlpv ] [ files...  ]**                                     |                                        |                                                                              |                     |
|          | t                                                                         | --tabular                              |                                                                              |                     |
|          |                                                                           |                                        |                                                                              |                     |
|          |                                                                           |                                        |                                                                              |                     |

**Note**:
    - chmod MODE  - '[ugoa]*([-+=]([rwxXst]*|[ugo]))+|[-+=][0-7]+'
        + chmod     777     a.txt
        + chmod     u+a     a.txt
        + chmod     u+s     a.txt
        + chmod     +t      a.txt
        + chmod     4755    a.txt # 2755 or 1711
    - umask
        + dir default = 777 -umask,  file default = 666 -umask,
        + SUID 4, SGID 2, Sticky 1
    - chattr mode -  +-=[aAcCdDeFijPsStTu]
    - ACL (Access control list)
        The output format of getfacl is as follows:
               1:  # file: somedir/
               2:  # owner: lisa
               3:  # group: staff
               4:  # flags: -s-
               5:  user::rwx
               6:  user:joe:rwx               #effective:r-x
               7:  group::rwx                 #effective:r-x
               8:  group:cool:r-x
               9:  mask::r-x
              10:  other::r-x
              11:  default:user::rwx
              12:  default:user:joe:rwx       #effective:r-x
              13:  default:group::r-x
              14:  default:mask::r-x
              15:  default:other::---
        ACL ENTRIES:

<!-- TODO: ACL -->