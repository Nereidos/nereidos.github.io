---
layout: post
category: Linux Guides
---

## Using the DD command in Terminal
### Write Image Files
"The basic use of the dd command is rather easy because it takes just two arguments: if= to specify the input file and of= to specify the output file. [Source](https://linoxide.com/linux-dd-command-create-1gb-file/)
```
 dd if=<source file name> of=<target file name> [Options]
```
Use lsblk to List Block Device in Linux: [Source](https://linoxide.com/lsblk-command-in-linux-list-block-devices/)
 lsblk
Example for flashing an .img on a SD-Card (use status=progress to see the flashing process):
```
 dd if=/opt/local/Downloads/file.img of=/dev/sdb status=progress
```
### Erase Disk with DD
Wipe Entire Disk
Filling the disk with all zeros:
```
 dd if=/dev/zero of=/dev/sdX bs=1M
```
Filling the disk with all random data:
```
 dd if=/dev/urandom of=/dev/sdX bs=1M
```
Wipe Master Boot Record (MBR)
```
 dd if=/dev/zero of=/dev/hdX bs=446 count=1
```
If you messed up your master boot record (MBR) you can wipe it using this command.

### Backing up a disk partition
Let’s say that our system has a separate partition for our home directory at ‘sda2’ and we want to back it up to a file named ‘home_backup.img’ in our current directory. Create an ‘.img’ (raw disk image) file:
```
dd if=/dev/sda2 of=home_backup.img
```
### Clone disks
It will copy the entire contents of the drive, not just the data. Make sure thers enough space on your output file.Re-partitioning the drive to the exact size currently filled by data can be very useful.
identify your disks:
```
 sudo fdisk -l 
``` 
Run this command:
```
 sudo dd if=/dev/sda of=/dev/sdb
```
---

## Scrub
### Erase Disks
 scrub [option] <target>

#### Available patterns are:
```
  -v, --version           display scrub version and exit
  -p, --pattern pat       select scrub pattern sequence
  -b, --blocksize size    set I/O buffer size (default 4m)
  -s, --device-size size  set device size manually
  -X, --freespace dir     create dir+files, fill until ENOSPC, then scrub
  -D, --dirent newname    after scrubbing file, scrub dir entry, rename
  -f, --force             scrub despite signature from previous scrub
  -S, --no-signature      do not write scrub signature after scrub
  -r, --remove            remove file after scrub
  -L, --no-link           do not scrub link target
  -R, --no-hwrand         do not use a hardware random number generator
  -t, --no-threads        do not compute random data in a parallel thread
  -n, --dry-run           verify file arguments, without writing
  -h, --help              display this help message
```
### Diffrent OPTIONS
```
  -v, --version           display scrub version and exit
  -p, --pattern pat       select scrub pattern sequence
  -b, --blocksize size    set I/O buffer size (default 4m)
  -s, --device-size size  set device size manually
  -X, --freespace dir     create dir+files, fill until ENOSPC, then scrub
  -D, --dirent newname    after scrubbing file, scrub dir entry, rename
  -f, --force             scrub despite signature from previous scrub
  -S, --no-signature      do not write scrub signature after scrub
  -r, --remove            remove file after scrub
  -L, --no-link           do not scrub link target
  -R, --no-hwrand         do not use a hardware random number generator
  -t, --no-threads        do not compute random data in a parallel thread
  -n, --dry-run           verify file arguments, without writing
  -h, --help              display this help message
```
### Using dod for example

#### dry-run
But first do **dry-run** to verify file arguments, without writing:
```
 scrub -p dod /dev/sdb -n
```
#### Execute
then use:
 scrub -p dod /dev/sdb
Output:
```
 scrub: using DoD 5220.22-M patterns
 scrub: please verify that device size below is correct!
 scrub: scrubbing /dev/sdb 250047627776 bytes (~232GB)
 scrub: random  |................................................|   
 scrub: 0x00    |................................................|
 scrub: 0xff    |................................................|
 scrub: verify  |................................................|
```
## Create Partition and Format the Filesystem==
After you wiped your disk, you probably need to create a Partition and a proper Filesystem.
Here you will find everything you need to proceed: [[Create Partition and Format the Filesystem]]

## Useful Links and Sources
### DD
- [https://linoxide.com/linux-dd-command-create-1gb-file/](https://linoxide.com/linux-dd-command-create-1gb-file/)
- [https://www.looklinux.com/how-to-wipe-hard-drive-clean-using-dd-command-in-linux/](https://www.looklinux.com/how-to-wipe-hard-drive-clean-using-dd-command-in-linux/)
- [https://linoxide.com/commands-wipe-disk-linux/](https://linoxide.com/commands-wipe-disk-linux/)
- [https://linuxhandbook.com/dd-command/](https://linuxhandbook.com/dd-command/)
### Scrub
- [https://unix.cafe/wp/en/2020/07/securely-remove-files-using-scrub-tool/](https://unix.cafe/wp/en/2020/07/securely-remove-files-using-scrub-tool/)
### Lsblk
- [https://linoxide.com/lsblk-command-in-linux-list-block-devices/](https://linoxide.com/lsblk-command-in-linux-list-block-devices/)
