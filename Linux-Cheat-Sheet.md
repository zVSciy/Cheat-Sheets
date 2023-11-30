# Linux Cheat Sheet v1.01
## Table of Contents
- **[Shortcuts](#shortcuts)** 
- **[Navigation](#navigation)**
- **[Flow Control, Chains, Remote Access and File transportation](#flow-control-chains-remote-access-and-file-transportation)**
- **[File Manipulation](#file-manipulation)**
- **[File Research](#file-research)**
- **[File-Permission](#file-permission)**
- **[User and Group management](#user-and-group-management)**
- **[Archive and compress Data](#archive-and-compress-data)**
- **[Extract, sort and filter Data]()**
- **[Mounting, Formatting and Partitioning]()**
- **[Process Management]()**
---
### Shortcuts
```
!!                                      | repeat your last command
```
```
↑ or ↓                                  | navigate through your previous commands
```
```
Ctrl + A                                | cursor to the beginning of the commands
```
```
Ctrl + C                                | kills running processes in the terminal
```
```
Ctrl + D                                | log out
```
```
Ctrl + E                                | cursor to the end of the line
```
```
Ctrl + K                                | delete behind your cursor
```
```
Ctrl + L                                | clear the therminal
```
```
Ctrl + U                                | delete in front your cursor
```
```
Ctrl + W                                | delete the word left your cursor
```
```
Ctrl + Z                                | stops the running command
```
---
### Navigation
```
cd <directory>                          | change directory
```
```
cd “<directoryNameWithSpaces>”          | change directory
```
```
cd ..                                   | back one directory (multiple times possible)
```
```
cd /                                    | Move back to the root
```
```
pwd                                     | print working directory
```
```
ls                                      | list current directory
```
```
ls <directory>                          | list files in a directory
```
```
ls -l                                   | list current directory with more information
```
```
ls -a                                   | list current directory + hidden files
```
```
ls -d <directory>                       | lists the directory itself
```
```
ls -R <directory>                       | lists the directory recursively
```
```
du -h                                   | disk usage of a directory
```
```
du -ah                                  | disk usage of directories and files
```
```
man <command>                           | list the manual of a command
```
---
### Flow Control, Chains, Remote Access and File transportation
```
<command> > <file>                      | redirect stdout to a file
```
```
<command> >> <file>                     | redirect stdout to a file and append it
```
```
<command> 2> <file>                     | redirect stderr to a file
```
```
<command> 2>> <file>                    | redirect stderr to a file and append it
```
```
<command> 2> /dev/null                  | redirect stderr to /dev/null (linux’ bin)
```
```
<command> &> <file>                     | redirect stdout and stderr to a file
```
```
<command> &>> <file>                    | redirect stdout and stderr to a file and append it
```
```
<command1> | <command2>                 | allows to execute two commands at the same
                                          time by sending the stdout of the first
                                          command to stdin of the other one
```
---
### File Manipulation
```
cp <file> <new file>                    | copy a file
```
```
cp -r <directory> <new directory>       | copy directory
```
```
mv <file> <dest.Path>                   | move a file
```
```
mv -r <directory> <dest.Path>           | move a directory
```
```
rm <file>                               | delete a file
```
```
rm -r <directory>                       | delete a directory
```
```
rm -f <directory>                       | delete without asking again (forcing)
```
```
rm -d <directory>                       | delete empty directory
```
```
touch <filePath/Name>                   | create a new file 
```
```
mkdir <directory>                       | create a new directory
```
```
mkdir -p <directory>                    | creates parent-directories as well 
```
```
cat <textfile>                          | prints input of a textfile
```
```
cat -n <textfile>                       | number of output-lines
```
```
cat -b <textfile>                       | number of non-empty output-lines
```
```
cat -s <textfile>                       | squeezes duplicated lines
```
```
head <textfile>                         | print the first 10 lines     
```
```
head -<number> <textfile>               | print a specific amount from the top
```
```
tail <textfile>                         | print the last 10 lines
```
```
tail -<number> <textfile>               | print a specific amount from the bottom
```
```
ln <file1> <file2>                      | create a hardlink
```                                   
```
ln -s <file1> <file2>                   | create a softlink
```
```
file <file>                             | display the real file-typ
```
```
file -z <file>                          | display the real file-typ in a compressed file
```
---
### File Research
```
locate <string>                         | return the file with matching content
```
```
locate <file>                           | search local DB for matching file
```
```
locate -d <file>                        | search an extern DB
```
```
locate -i <file>                        | ignore lower and upper cases
```
```
updated                                 | update local DB
```
```
find [*]<file>[*]                       | search for files on the FS in real time
```
```
find -name “[*]<letter(s)>[*]”          | search for files with x
```
```
find <file> -exec <command> \;          | execute a command on found files
```
```
find <file> -delete                     | delete the found files
```
```
find <file> -ls                         | list the found files
```
```
find <source> -size +|-<fileSize>       | files with a size greater/smaller x
```
```
find <source> -type d                   | search only for directories
```
```
find <source> -type f                   | search only for files
```
```
find <source> -atime +|-<amount>        | files with an access-time greater/smaller x
```
```
find <source> -amin <minutes>           | files accessed in the last x minutes
```
```
find <source> -mtime <days>             | files changed in the last x days
```
```
find <source> -mmin <minutes>           | files changed in the last x minutes
```
```
find <source> -empty                    | files/directories which are empty
```
```
find <source> -gid|-group <x>           | files with the groupID/groupName x
```
```
find <source> -uid|-user <x>            | files with the userID/username x
```
```
find <source> -writable                 | files which are able to be written
```
```
man find                                | for further information
```
---
### File-Permission
```
chown <owner>:<group> <file/dir>        | change ownership of a file/directory
```
```
chown -R <owner>:<group> <dir>          | change ownership of a directory recursively
```
```
chmod <permission> <file/dir>           | change permission on a file or directory
```
```
chmod -R <permission> <file/dir>        | change permission on a directory recursively
```
```
<permission> => abc                     | separated in three bits
```
```
a                                       | specification-bit for owner-permission (0-7)
``` 
```
b                                       | specification-bit for group-permission (0-7)
```
```
c                                       | specification-bit for others (0-7)
```
```
1                                       | execute-bit
```
```
2                                       | write-bit
```
```
4                                       | read-bit
```
---
### User and Group Management
```
useradd <login>                         | create a new user
```
```
usermod -aG <group(s)>                  | append secondary group to the existing ones
```
```
usermod -l <newLogin> <login>           | change a user’s login
```
```
usermod -m <login>                      | move contents from homedir to other location
```
```
useradd/mod -c <name> <login>           | create/modify user + name
```
```
useradd/mod -d <directory> <login>      | create/modify user + specify homedir.
```
```
useradd/mod -g <group> <login>          | create/modify user + primary group
```
```
useradd/mod -G <group(s)> <login>       | create/modify user + secondary group(s)
```
```
useradd/mod -p <passwd> <login>         | create/modify user + password
```
```
useradd/mod -s <shell> <login>          | create/modify user + login shell
```
```
useradd/mod -u <uid> <login>            | create/modify user with specific UID
```
```
userdel <login>                         | delete user
```
```
userdel -f <login>                      | force userdel even if he’s logged in
```
```
userdel -r <login>                      | delete user’s homedir as well
```
```
groupadd <name>                         | create a new group
```
```
groupmod -n <newName> <name>            | modify a group’s name
```
```
groupadd/mod -g <gid> <name>            | create/modify group with its GID
```
```
groupdel <name>                         | delete a group
```
```
passwd <login/name>                     | change password for a user/group
```
---
### Archive and compress Data
```
tar -cvzf <archive> <source>            | create a compressed archive
```
```
tar -rvf <archive> <files>              | add files to uncompressed archive
```
```
tar -tf <archive>                       | show contents of the archive
```
```
tar -xvzf <archive> -C <destination>    | extract and unzip archive to a destination
```
```
tar -uf <archive> <files>               | update similar files in an unzip archive
```
```
gzip <archive>                          | compress archive to a .tar.gz-file
```
```
gzip -r <archive>                       | compress archive recursively
```
```
gunzip <archive>                        | unzip a compressed archive
```
```
gunzip -r <archive>                     | unzip a compressed archive recursively
```
---
### Extract, sort and filter Data
#### Extract data
```
head <textfile>                         | print the first 10 lines     
```
```
head -<number> <textfile>               | print a specific amount from the top
```
```
tail <textfile>                         | print the last 10 lines
```
```
tail -<number> <textfile>               | print a specific amount from the bottom
```
#### Sort Data
```
sort <file>                             | sort lines of text files
```
```
sort -r <file>                          | reverse the order while sorting
```
```
sort -k <column_number> <file>          | sort based on a specific column
```
#### Filter data
```
grep '<pattern>' <file>                | search for a pattern in a file
```
```
grep -i '<pattern>' <file>             | case-insensitive pattern search
```
```
grep -v '<pattern>' <file>             | display lines not containing the pattern
```
```
awk '/<pattern>/' <file>               | pattern scanning and processing language
```
```
sed -n '/<pattern>/p' <file>           | stream editor for filtering and transforming text
```
```
cut -f <column_number> <file>          | remove sections from each line of a file
```
---
### Mounting, Formatting and Partitioning
#### Mounting
```
mount /dev/sdX1 /mnt                 | mount the partition /dev/sdX1 to the /mnt directory
```
```
mount -t ext4 /dev/sdX1 /mnt         | mount with a specific file system type (ext4 in this case)
```
```
umount /mnt                          | unmount the file system mounted on /mnt
```
#### Formatting
```
mkfs.ext4 /dev/sdX1                  | format the partition /dev/sdX1 as ext4
```
```
mkfs.ntfs /dev/sdX1                  | format the partition /dev/sdX1 as NTFS
```
```
mkswap /dev/sdX1                     | create a swap area on /dev/sdX1
```
#### Partitioning
```
fdisk /dev/sdX                       | start the fdisk utility for partitioning /dev/sdX
```
```
gparted                              | open the GParted graphical partition editor
```
```
parted /dev/sdX                      | command-line partitioning tool
```
```
gdisk /dev/sdX                       | GPT partitioning tool for GUID Partition Table
```
```
lsblk                                | list information about block devices, including partitions
```
---
Give the most important Linux commands of Process Management in stile like that:
### Process Management
#### List Running Processes
```
ps                                   | display information about active processes  
```
```
ps aux                               | detailed list of all processes
```
```
top                                  | dynamic real-time view of running processes
```
```
htop                                 | interactive process viewer
```
#### Kill or Signal Processes
```
kill <PID>                           | send a signal to terminate a process with a specific PID  
```
```
killall <process_name>               | send a signal to terminate all processes with a specific name

```
```
pkill <process_name>                 | signal processes based on name
```
```
kill -9 <PID>                        | forcefully terminate a process
```
#### Background and Foreground
```
<command> &                          | run a command in the background
```
```
bg                                  | list stopped or background jobs
```
```
fg                                  | bring a background job to the foreground
```
#### Job Control
```
jobs                                | display a list of jobs 
```
```
bg %<job_number>                    | run a stopped job in the background
```
```
fg %<job_number>                    | bring a job to the foreground
```
```
Ctrl + Z                            | suspend a foreground process
```
#### System Resource Monitoring
```
free                                | display amount of free and used memory  
```
```
uptime                              | show how long the system has been running
```
```
vmstat                              | virtual memory statistics
```
```
iostat                              | report CPU statistics and input/output statistics for devices and partitions
```
---
