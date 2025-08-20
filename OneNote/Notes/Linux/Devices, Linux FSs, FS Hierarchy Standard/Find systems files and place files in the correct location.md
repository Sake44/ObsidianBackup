Linux distributions come in all shapes and sizes, but one thing that almost all of them share is that
they follow the Filesystem Hierarchy Standard (FHS), which defines a “standard layout” for the filesystem, making interoperation and system administration much easier.

## The FHS
The Filesystem Hierarchy Standard (FHS) is an effort by the Linux Foundation to standardize the
directory structure and directory contents on Linux systems.

More information here: [FHS Referenced Specifications](https://refspecs.linuxfoundation.org/fhs.shtml)

According to the standard, the basic directory structure is as follows:
```
/
```
This is the root directory, the topmost directory in the hierarchy. Every other directory is located inside it. A filesystem is often compared to a “tree”, so this would be the “trunk” to which all branches are connected.
```
/bin
```
Essential binaries, available to all users.
```
/boot
```
Files needed by the boot process, including the Initial RAM Disk (initrd) and the Linux kernel
itself.
```
/dev
```
Device files. These can be either physical devices connected to the system (for example,
/dev/sda would be the first SCSI or SATA disk) or virtual devices provided by the kernel.
```
/etc
```
Host-specific configuration files. Programs may create subdirectories under /etc to store
multiple configuration files if needed.
```
/home
```
Each user in the system has a “home” directory to store personal files and preferences, and
most of them are located under /home. Usually, the home directory is the same as the
username, so the user John would have his directory under /home/john. The exceptions are
the superuser (root), which has a separate directory (/root) and some system users.
```
/lib
```
Shared libraries needed to boot the operating system and to run the binaries under /bin and
/sbin.
```
/media
```
User-mountable removable media, like flash drives, CD and DVD-ROM readers, floppy disks,
memory cards and external disks are mounted under here.
```
/mnt
```
Mount point for temporarily mounted filesystems.
```
/opt
```
Application software packages.
```
/root
```
Home directory for the superuser (root).
```
/run
```
Run-time variable data.
```
/sbin
```
System binaries.
```
/srv
```
Data served by the system. For example, the pages served by a web server could be stored
under /srv/www.
```
/tmp
```
Temporary files.
```
/usr
```
Read-only user data, including data needed by some secondary utilities and applications.
```
/proc
```
Virtual filesystem containing data related to running processes.
```
/var
```
Variable data written during system operation, including print queue, log data, mailboxes,
temporary files, browser cache, etc.

### Temporary Files
Temporary files are files used by programs to store data that are only needed for a short time.
This can be the data of running processes, crash logs, scratch files from an autosave, intermediary
files used during a file conversion, cache files and such.

#### Location of tmp
Version 3.0 of the Filesystem Hierarchy Standard (FHS) defines standard locations for temporary files on Linux systems. Each location has a different purpose and behavior, and it is recommended that developers follow the conventions set by the FHS when writing temporary data to disk.
```
/tmp
```
According to the FHS, programs should not assume that files written here will be preserved
between invocations of a program. The recommendation is that this directory be cleared (all
files erased) during system boot-up, although this is not mandatory.
```
/var/tmp
```
Another location for temporary files, but this one should not be cleared during the system bootup.
Files stored here will usually persist between reboots.
```
/run
```
This directory contains run-time variable data used by running processes, such as process
identifier files (.pid). Programs that need more than one run-time file may create subdirectories here. This location must be cleared during system boot-up.

### Finding Files
To search for files on a Linux system, you can use the find command. This is a very powerful tool,
full of parameters that can suit its behaviour and modify output exactly to your needs.
To start, find needs two arguments: a starting point and what to look for. For example, to search
for all files in the current directory (and subdirectories) whose name ends in .jpg you can use:
```
find . -name '*.jpg'
```

If we want to check a pattern like 'anything.jpg anything' we can: 
```
find . -name '*.jpg*'
```

By default, find will begin at the starting point and descend through any subdirectories (and
subdirectories of those subdirectories) found. You can restrict this behaviour with the -maxdepth
N parameters, where N is the maximum number of levels.

### Searching for attributes
You can use the parameters below to search for files with specific attributes, like ones that are
writable by your user, have a specific set of permissions or are of a certain size:
```
-user USERNAME
```
Matches files owned by the user USERNAME.
```
-group GROUPNAME
```
Matches files owned by the group GROUPNAME.
```
-readable
```
Matches files that are readable by the current user.
```
-writable
```
Matches files that are writable by the current user.
```
-executable
```
Matches files that are executable by the current user. In the case of directories, this will match
any directory that the user can enter (x permission).
```
-perm NNNN
```
This will match any files that have exactly the NNNN permission. For example, -perm 0664 will
match any files which the user and group can read and write to and which others can read (or
rw-rw-r--).
You can add a - before NNNN to check for files that have at least the permission specified. For
example, -perm -644 would match files that have at least 644 (rw-r—r--) permissions. This
includes a file with 664 (rw-rw-r--) or even 775 (rwxrwx-r-x).
```
-empty
```
Will match empty files and directories.
```
-size N
```
Will match any files of N size, where N by default is a number of 512-byte blocks. You can add
suffixes to N for other units: Nc will count the size in bytes, Nk in kibibytes

### Searching by Time
Besides searching for attributes you can also perform searches by time, finding files that were
accessed, had their attributes changed or were modified during a specific period of time.
```
-amin N, -cmin N, -mmin N
```
This will match files that have been accessed, had attributes changed or were modified
(respectively) N minutes ago.
```
-atime N, -ctime N, -mtime N
```
This will match files that were accessed, had attributes changed or were modified N*24 hours
ago.

### Using locate and updatedb
locate and updatedb are commands that can be used to quickly find a file matching a given
pattern on a Linux system. But unlike find, locate will not search the filesystem for the pattern:
instead, it looks it up on a database built by running the updatedb command.
The simplest way to use locate is to just give it a pattern to search for.
Remember that with #locate you are matching patterns, not file extensions.
By default the pattern is case sensitive. To avoid this, you can pass -i parameter. 
When using multiple patterns, you can request locate to show only files that match all of them.
This is done with the -A option.
If you wish to count the number of files that match a given pattern instead of showing their full
path you can use the -c option.
One problem with locate is that it only shows entries present in the database generated by updatedb (located in /var/lib/mlocate.db). If the database is outdated, the output could show
files that have been deleted since the last time it was updated. One way to avoid this is to add the
-e parameter, which will make it check to see if the file still exists before showing it on the output.

#### Controlling behavior of updatedb

The behavior of updatedb can be controlled by the file /etc/updatedb.conf. This is a text file
where each line controls one variable. Blank lines are ignored and lines that start with the #
character are treated as comments.
```
PRUNEFS=
```
Any filesystem types indicated after this parameter will not be scanned by updatedb. The list
of types should be separated by spaces, and the types themselves are case-insensitive, so NFS
and nfs are the same.
```
PRUNENAMES=
```
This is a space-separated list of directory names that should not be scanned by updatedb.
```
PRUNEPATHS=
```
This is a list of path names that should be ignored by updatedb. The path names must be
separated by spaces and specified in the same way they would be shown by updatedb (for
example, /var/spool /media)
```
PRUNE_BIND_MOUNTS=
```
This is a simple yes or no variable. If set to yes bind mounts (directories mounted elsewhere
with the mount --bind command) will be ignored.

### Finding Binaries, Manual Pages and Source Code
Which is a very useful command that shows the full path to an executable.
```
which bash
```
If the -a option is added the command will show all pathnames that match the executable.
#type is a similar command which will show information about a binary, including where it is
located and its type.
The -a parameter works in the same way as in which, showing all pathnames that match the
executable.
And the -t parameter will show the file type of the command which can be alias, keyword,
function, builtin or file.
The command #whereis is more versatile and besides binaries can also be used to show the
location of man pages or even source code for a program
You can quickly filter the results using commandline switches like -b, which will limit them to
only the binaries, -m, which will limit them to only man pages, or -s, which will limit them to only
the source code.