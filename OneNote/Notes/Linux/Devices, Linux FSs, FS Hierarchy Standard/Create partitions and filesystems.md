On any operating system, a disk needs to be partitioned before it can be used. A partition is a logical subset of the physical disk, and information about partitions are stored in a partition table.
Usually each partition is seen by an operating system as a separate “disk”, even if they all reside in
the same physical media. On Windows systems they are assigned letters like C: (historically the main disk), D: and so on. On Linux each partition is assigned to a directory under /dev, like
/dev/sda1 or /dev/sda2.

# Understanding MBR and GPT
There are two main ways of storing partition information on hard disks. The first one is MBR
(Master Boot Record), and the second one is GPT (GUID Partition Table).

###### **MBR**
This is a remnant from the early days of MS-DOS (more specifically, PC-DOS 2.0 from 1983) and
for decades was the standard partitioning scheme on PCs. The partition table is stored on the first sector of a disk, called the Boot Sector, along with a boot loader, which on Linux systems is usually the GRUB bootloader. But MBR has a series of limitations that hinder its use on modern systems, like the inability to address disks of more than 2 TB in size, and the limit of only 4 primary partitions per disk.

###### GUID
A partitioning system that addresses many of the limitations of MBR. There is no practical limit
on disk size, and the maximum number of partitions are limited only by the operating system
itself. It is more commonly found on more modern machines that use UEFI instead of the old PC
BIOS.

## Managing MBR partitions with FDISK
The standard utility for managing MBR partitions on Linux is fdisk. This is an interactive, menu-driven utility.
```
fdisk <device>

Welcome to fdisk (util-linux 2.33.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Command (m for help):
```
Keep in mind that you need to specify the device corresponding to the physical disk, not one of its
partitions (like /dev/sda1).

### Printing the Current Partition Table
The command **p** is used to print the current partition table. The output is something like this:
```
Command (m for help): p

Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Disk model: CT120BX500SSD1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x97f8fef5

Device    Boot     Start       End   Sectors   Size Id Type
/dev/sda1           4096 226048942 226044847 107.8G 83 Linux
/dev/sda2      226048944 234437550   8388607     4G 82 Linux swap / Solaris
```

### Primary vs Extended Partitions
On an MBR disk, you can have 2 main types of partitions, primary and extended. Like we said
before, you can have only 4 primary partitions on the disk, and if you want to make the disk “bootable”, the first partition must be a primary one.

One way to work around this limitation is to create an extended partition that acts as a container
for logical partitions.

### Creating a Partition
To create a partition, use the n command. By default, partitions will be created at the start of unallocated space on the disk. You will be asked for the partition type (primary or extended), first
sector and last sector.
For the first sector, you can usually accept the default value suggested by fdisk, unless you need
a partition to start at a specific sector. Instead of specifying the last sector, you can specify a size followed by the letters K, M, G, T or P (Kilo, Mega, Giga, Tera or Peta).
Below an example for the creation of a primary partition: 
```
Command (m for help): n

Partition type
p primary (0 primary, 0 extended, 4 free)
e extended (container for logical partitions)
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-3903577, default 2048): 2048
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-3903577, default 3903577): +1G
```

To check for how much disk space is on the disk, you can use the F command: 
```
Command (m for help): F
```

### Deleting Partitions
To delete a partition, use the d command. fdisk will ask you for the number of the partition you
want to delete, unless there is only one partition on the disk.

Keep in mind that when creating a new partition with fdisk, the maximum size will be limited to
the maximum amount of contiguous unallocated space on the disk. Say, for example, that you
have the following partition map:
```
Device       Boot   Start     End Sectors Size Id Type
/dev/sdd1            2048 1050623 1048576 512M 83 Linux
/dev/sdd2         1050624 2099199 1048576 512M 83 Linux
/dev/sdd3         2099200 3147775 1048576 512M 83 Linux
```

Then you delete partition 2 and check for free space: 
```
Command (m for help): F

Unpartitioned space /dev/sdd: 881 MiB, 923841536 bytes, 1804378 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

  Start     End Sectors Size
1050624 2099199 1048576 512M
3147776 3903577 755802  369M
```

Adding up the size of the unallocated space, in theory we have 881 MB available. But see what
happens when we try to create a 700 MB partition:
```
Command (m for help): n

Partition type
	p primary (2 primary, 0 extended, 2 free)
	e extended (container for logical partitions)
Select (default p): p
Partition number (2,4, default 2): 2
First sector (1050624-3903577, default 1050624):
Last sector, +/-sectors or +/-size{K,M,G,T,P} (1050624-2099199, default 2099199): +700M
Value out of range.
```
That happens because the largest contiguous unallocated space on the disk is the 512 MB block that belonged to partition 2. Your new partition cannot “reach over” partition 3 to use some of the
unallocated space after it.

### Changing the Partition Type

Occasionally, you may need to change the partition type, especially when dealing with disks that will be used on other operating systems and platforms. This is done with the command t, followed
by the number of the partition you wish to change.

The partition type must be specified by its corresponding hexadecimal code, and you can see a list of all the valid codes by using the command **l**.


## Managing GUID Partitions with GDISK
The utility gdisk is the equivalent of fdisk when dealing with GPT partitioned disks. In fact, the
interface is modeled after fdisk, with an interactive prompt and the same (or very similar) commands.

### Printing the Current Partition
The command p is used to print the current partition table.
```
Command (? for help): p

Disk /dev/sdb: 3903578 sectors, 1.9 GiB
Model: DataTraveler 2.0
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): AB41B5AA-A217-4D1E-8200-E062C54285BE
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 3903544
Partitions will be aligned on 2048-sector boundaries
Total free space is 1282071 sectors (626.0 MiB)
Number Start (sector) End (sector)       Size Code Name
  1     2048               2099199 1024.0 MiB 8300 Linux filesystem
  2  2623488               3147775  256.0 MiB 8300 Linux filesystem
```

Right from the start, we notice a few different things:
- Each disk has a unique Disk Identifier (GUID). This is a 128 bit hexadecimal number, assigned
  randomly when the partition table is created. Since there are 3.4 × 1038 possible values to this
  number, the chances that 2 random disks have the same GUID are pretty slim.
- See the phrase Partition table holds up to 128 entries? That’s right, you can have up
  to 128 partitions on a GPT disk. Because of this, there is no need for primary and extended partitions

### Creating a Partition
The command to create a partition is n, just as in fdisk. The main difference is that besides the
partition number and the first and last sector (or size), you can also specify the partition type during the creation. GPT partitions support many more types than MBR. You can check a list of all
the supported types by using the l command.

### Deleting a Partition
To delete a partition, type d and the partition number. Unlike fdisk, the first partition will not be
automatically selected if it is the only one on the disk.
On GPT disks, partitions can be easily reordered, or “sorted”, to avoid gaps in the numbering
sequence. To do this, simply use the s command.

So if you delete, for example, the second partition of three and then use the command **s**, the partition number will be reordered and the old third partition will become the second one. 

Unlike MBR disks, when creating a partition on GPT disks the size is not limited by the maximum
amount of contiguous unallocated space. You can use every last bit of a free sector, no matter
where it is located on the disk.

### Recovery Options
GPT disks store backup copies of the GPT header and partition table, making it easy to recover
disks in case this data has been damaged. gdisk provides features to aid in those recovery tasks,
accessed with the r command.

Ypu can rebuild a corrupt main GPT header or partition table with **b** and **c**, or use the main header and table to rebuild a backup with **d** and **e**.
You can also convert a MBR to a GPT with **f**, and do the opposite with **g**, among other operations.

# Creating File Systems

Partitioning the disk is only the first step towards being able to use a disk. After that, you will need
to format the partition with a filesystem before using it to store data.
A filesystem controls how the data is stored and accessed on the disk. Linux supports many filesystems, some native, like the ext (Extended Filesystem) family, while others come from other operating systems like FAT from MS-DOS, NTFS from Windows NT, etc.

## Creating an ext2/ext3/ext4 Filesystem
The Extended Filesystem (ext) was the first filesystem for Linux, and through the years was replaced by new versions called ext2, ext3 and ext4, which is currently the default filesystem for
many Linux distributions.

The utilities mkfs.ext2, mkfs.ext3 and mkfs.ext4 are used to create ext2, ext3 and ext4 filesystems. All of those "utilities" exist only as symbolic links to another utility called mke2fs.mke2fs

The most simply form of usage is: 
```
mkfs.ext2 TARGET
```
Where TARGET is the name of the partition where the FS should be created.

Instead of using the command corresponding to the filesystem you wish to create, you can pass
the -t parameter to mke2fs followed by the filesystem name.

### Command Line as Parameters
mke2fs supports a wide range of command line parameters and options. Here are some of the
most significant ones: 

```
-b SIZE
```
Sets the size of the data blocks in the device to SIZE, which can be 1024, 2048 or 4096 bytes per
block.
```
-c
```
Checks the target device for bad blocks before creating the filesystem. You can run a thorough,
but much slower check by passing this parameter twice, as in mkfs.ext4 -c -c TARGET.
```
-d DIRECTORY
```
Copies the contents of the specified directory to the root of the new filesystem. Useful if you
need to “pre-populate” the disk with a predefined set of files.
```
-F
```
Danger, Will Robinson! This option will force mke2fs to create a filesystem, even if the other
options passed to it or the target are dangerous or make no sense at all. If specified twice (as in
-F -F) it can even be used to create a filesystem on a device which is mounted or in use, which
is a very, very bad thing to do.
```
-L VOLUME_LABEL
```
Will set the volume label to the one specified in VOLUME_LABEL. This label must be at most 16 characters long.
```
-n
```
This is a truly useful option that simulates the creation of the filesystem, and displays what
would be done if executed without the n option. Think of it as a “trial” mode. Good to check
things out before actually committing any changes to disk.
```
-q
```
Quiet mode. mke2fs will run normally, but will not produce any output to the terminal. Useful
when running mke2fs from a script.
```
-U ID
```
This will set the UUID (Universally Unique Identifier) of a partition to the value specified as ID.
UUIDs are 128 bit numbers in hexadecimal notation that serve to uniquely identify a partition
to the operating system. This number is specified as a 32-digit string in the format 8-4-4-4-12,
meaning 8 digits, hyphen, 4 digits, hyphen, 4 digits, hyphen, 4 digits, hyphen, 12 digits, like
D249E380-7719-45A1-813C-35186883987E. Instead of an ID you can also specify parameters
like clear to clear the filesystem UUID, random, to use a randomly generated UUID, or time to
create a time-based UUID.
```
-V
```
Verbose mode, prints much more information during operation than usual. Useful for
debugging purposes.

## Creating an XFS Filesystem
#XFS is a high-performance filesystem originally developed by Silicon Graphics in 1993 for its IRIX operating system. Due to its performance and reliability features, it is commonly used for servers and other environments that require high (or guaranteed) filesystem bandwidth.

Tools for managing XFS filesystems are part of the xfsprogs package. This package may need to
be installed manually, as it is not included by default in some Linux distributions. Others, like Red
Hat Enterprise Linux 7, use XFS as the default filesystem.
XFS filesystems are divided into at least 2 parts, a log section where a log of all filesystem
operations (commonly called a Journal) are maintained, and the data section.
The most basic command to create an XFS filesystem is mkfs.xfs TARGET, where TARGET is the
partition you want the filesystem to be created in. For example:
```
mkfs.xfs /dev/sda1
```

mkfs.xfs supports a number of command line options: 

```
-b size=VALUE
```
Sets the block size on the filesystem, in bytes, to the one specified in VALUE. The default value is
4096 bytes (4 KiB), the minimum is 512, and the maximum is 65536 (64 KiB).
```
-m crc=VALUE
```
Parameters starting with -m are metadata options. This one enables (if VALUE is 1) or disables
(if VALUE is 0) the use of CRC32c checks to verify the integrity of all metadata on the disk. This
enables better error detection and recovery from crashes related to hardware issues, so it is
enabled by default. The performance impact of this check should be minimal, so normally
there is no reason to disable it.
```
-m uuid=VALUE
```
Sets the partition UUID to the one specified as VALUE. Remember that UUIDs are 32-character
(128 bits) numbers in hexadecimal base, specified in groups of 8, 4, 4, 4 and 12 digits separated
by dashes, like 1E83E3A3-3AE9-4AAC-BF7E-29DFFECD36C0.
```
-f
```
Force the creation of a filesystem on the target device even if a filesystem is detected on it.
```
-l logdev=DEVICE
```
This will put the log section of the filesystem on the specified device, instead of inside the data
section.
```
-l size=VALUE
```
This will set the size of the log section to the one specified in VALUE. The size can be specified in
bytes, and suffixes like m or g can be used. -l size=10m, for example, will limit the log section
to 10 Megabytes.
```
-q
```
Quiet mode. In this mode, mkfs.xfs will not print the parameters of the file system being
created.
```
-L LABEL
```
Sets the filesystem label, which can be at most 12 characters long.
```
-N
```
Similar to the -n parameter of mke2fs, will make mkfs.xfs print all the parameters for the creation of the file system, without actually creating it. 

## Creating a FAT or VFAT Filesystem

The #FAT filesystem originated from MS-DOS, and through the years has received many revisions
culminating on the FAT32 format released in 1996 with Windows 95 OSR2.
#VFAT is an extension of the FAT16 format with support for long (up to 255 characters) file names.
Both filesystems are handled by the same utility, mkfs.fat. mkfs.vfat is an alias to it.

The FAT filesystem has important drawbacks which restrict its use on large disks. FAT16, for example, supports volumes of at most 4 GB and a maximum file size of 2 GB. FAT32 ups the
volume size to up to 2 PB, and the maximum file size to 4 GB.

The most basic command for the creation of a FAT filesystem is mkfs.fat TARGET, where TARGET
is the partition you want the filesystem to be created in. For example:
```
mkfs.fat /dev/sdc1
```

## Creating an exFAT Filesystem
exFAT is a filesystem created by Microsoft in 2006 that addresses one of the most important
limitations of FAT32: file and disk size. On exFAT, the maximum file size is 16 exabytes (from 4 GB
on FAT32), and the maximum disk size is 128 petabytes.

The default utility for creating exFAT filesystems is mkfs.exfat, which is a link to mkexfatfs.
The most basic command is mkfs.exfat TARGET, where TARGET is the partition you want the
filesystem to be created in. For example:
```
mkfs.exfat /dev/sdb2
```
## Getting to know Btrfs Filesystem
#Btrfs is a filesystem that has been in development since 2007 specifically for Linux by the Oracle Corporation and other companies, including Fujitsu, Red Hat, Intel and SUSE, among others.
There are many features that make Btrfs attractive on modern systems where massive amounts of
storage are common.
As it is a copy-on-write filesystem it is very resilient to crashes. And on top of that, Btrfs is simple
to use, and well supported by many Linux distributions.

### Creating a Btrfs Filesystem

The utility mkfs.btrfs is used to create a Btrfs filesystem.
```
mkfs.btrfs /dev/sdb1
```

You can use the -L to set a label (or name) for your filesystem. Btrfs labels can have up to 256
characters.

Note this peculiar thing about Btrfs: you can pass multiple devices to the mkfs.btrfs command.
Passing more than one device will span the filesystem over all the devices which is similar to a
RAID or LVM setup. To specify how metadata will be distributed in the disk array, use the -m
parameter. Valid parameters are raid0, raid1, raid5, raid6, raid10, single and dup.
For example, to create a filesystem spanning /dev/sdb1 and /dev/sdc1, concatenating the two
partitions into one big partition, use:

```
mkfs.btrfs -d single /dev/sdb /dev/sdc
```

#### Managing Subvolumes
Subvolumes are like filesystems inside filesystems. Think of them as a directory which can be
mounted as (and treated like) a separate filesystem. Subvolumes make organization and system
administration easier, as each one of them can have separate quotas or snapshot rules.

Subvolumes are not partitions. A partition allocates a fixed space on a drive. This can lead to problems further down the line.
Suppose you have a Btrfs filesystem mounted on /mnt/disk, and you wish to create a subvolume
inside it to store your backups. Let’s call it BKP:
```
btrfs subvolume create /mnt/disk/BKP
```

Next we list the contents of the /mnt/disk filesystem. You will see that we have a new directory,
named after our subvolume.
```
ls -lh /mnt/disk
total 0
drwxr-xr-x 1 root root 0 jul 13 17:35 BKP

```

#### Working with Snapshots
Snapshots are just like subvolumes, but pre-populated with the contents from the volume from
which the snapshot was taken.

When created, a snapshot and the original volume have exactly the same content. But from that
point in time, they will diverge. Changes made to the original volume (like files added, renamed or
deleted) will not be reflected on the snapshot, and vice-versa.

Keep in mind that a snapshot does not duplicate the files, and initially takes almost no disk space.
It simply duplicates the filesystem tree, while pointing to the original data.

The command to create a snapshot is the same used to create a subvolume, just add the snapshot
parameter after btrfs subvolume. The command below will create a snapshot of the Btrfs filesystem mounted in /mnt/disk in /mnt/disk/snap:
```
btrfs subvolume snapshot /mnt/disk /mnt/disk/snap
```

It is also possible to create read-only snapshots. They work exactly like writable snapshots, with
the difference that the contents of the snapshot cannot be changed, they are “frozen” in time. Just
add the -r parameter when creating the snapshot.

##### Compression for btrfs
Btrfs supports transparent file compression, with three different algorithms available to the user.
This is done automatically on a per-file basis, as long as the filesystem is mounted with the -o
compress option. The algorithms are smart enough to detect incompressible files and will not try
to compress them, saving system resources. So on a single directory you may have compressed
and uncompressed files together.

# Managing Partitions with GNU Parted
