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

