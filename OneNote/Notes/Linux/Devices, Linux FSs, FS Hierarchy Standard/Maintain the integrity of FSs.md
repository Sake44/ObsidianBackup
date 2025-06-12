Modern Linux filesystems are journaled. This means that every operation is registered in an
internal log (the journal) before it is executed.

## Checking Disk Usage
There are two commands that can be used to check how much space is being used and how much
is left on a filesystem: 
- du (disk usage)
- df (disk free)
We can also use:
```
du -h
# to return in it in human readable
```
To show an individual count for all files in the directory, use the -a parameter.

You may wish to exclude some types of files from the count, which you can do with -exclude="PATTERN", where PATTERN is the pattern against which you wish to match. Consider
this directory:
```
du -ah --exclude="*.bin"
```

## Checking for Free Space
du works at the files level. There is another command that can show you disk usage, and how much space is available, at the filesystem level. This command is df.
The command df will provide a list of all of the available (already mounted) filesystems on your system.
```
df 

# Human readable
df -h
```
One useful parameter is -T, which will also print the type of each filesystem.
Showing only ext4 filesystems:
```
df -ht ext4
```
You can also customize the output of df, selecting what should be displayed and in which order, using the --output= parameter followed by a comma separated list of fields you wish to display.
Some of the available fields are:
```
source
```
The device corresponding to the filesystem.
```
fstype
```
The filesystem type.
```
size
```
The total size of the filesystem.
```
used
```
How much space is being used.
```
avail
```
How much space is available.
```
pcent
```
The usage percentage.
```
target
```
Where the filesystem is mounted (mount point).

## Maintaining ext2, ext3 and ext4 FSs
To check a filesystem for errors (and hopefully fix them), Linux provides the fsck utility. You can invoke it with #fsck followed by the filesystem's location you want to check: 
```
fsck /dev/sdb1
```

	NEVER run fsck (or related utilities) on a mounted filesystem. Data may be lost

fsck can take some command-line arguments. These are some of the most common:
```
-A
```
This will check all filesystems listed in /etc/fstab.
```
-C
```
Displays a progress bar when checking a filesystem. Currently only works on ext2/3/4
filesystems.
```
-N
```
This will print what would be done and exit, without actually checking the filesystem.
```
-R
```
When used in conjunction with -A, this will skip checking the root filesystem.
```
-V
```
Verbose mode, prints more information than usual during operation. This is useful for
debugging.
The specific utility for ext2, ext3 and ext4 filesystems is e2fsck. By default, it runs in interactive mode: when a filesystem error is found, it stops and asks the user what to do. The user must type y to fix the problem, n to leave it unfixed or a to fix the current problem and all subsequent ones.
There are also options that cause #e2fsck to run in non-interactive mode: 

```
-p
```
This will attempt to automatically fix any errors found. If an error that requires intervention
from the system administrator is found, e2fsck will provide a description of the problem and
exit.
```
-y
```
This will answer y (yes) to all questions.
```
-n
```
The opposite of -y. Besides answering n (no) to all questions, this will cause the filesystem to be
mounted read-only, so it cannot be modified.
```
-f
```
Forces e2fsck to check a filesystem even if is marked as “clean”, i.e. has been correctly
unmounted.

### Fine Tuning an ext FS
ext2, ext3 and ext4 filesystems have a number of parameters that can be adjusted, or “tuned”, by
the system administrator to better suit the system needs. The utility used to display or modify
these parameters is called tune2fs.
To see the current parameters for any given filesystem, use the -l parameter followed by the
device representing the partition.

### Maintaining XFS Filesystems
For XFS filesystems, the equivalent of fsck is #xfs_repair. If you suspect that something is wrong
with the filesystem, the first thing to do is to scan it for damage.
This can be done by passing the -n parameter to xfs_repair, followed by the device containing
the filesystem. The -n parameter means “no modify”: the filesystem will be checked, errors will be
reported but no repairs will be made.
To debug an XFS filesystem, the utility xfs_db can be used, like in xfs_db /dev/sdb1. This is
mostly used to inspect various elements and parameters of the filesystem.