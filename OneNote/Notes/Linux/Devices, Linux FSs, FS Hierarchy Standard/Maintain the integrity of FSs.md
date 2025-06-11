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
