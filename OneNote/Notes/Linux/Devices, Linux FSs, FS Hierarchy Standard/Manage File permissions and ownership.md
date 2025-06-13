Being a multi-user system, Linux needs some way to track who owns each file and whether or not
a user is allowed to perform actions on a file. This is to ensure the privacy of users who might want to keep the contents of their files confidential. 
This is done through a three-level permissions system. Every file on disk is owned by a user and a
user group and has three sets of permissions: one for its owner, one for the group who owns the
file and one for everyone else.
## Querying information about Files and Directories
The command **ls** is used to get a listing of the contents of any directory:
```
ls
```

To get more information for each file or directory we can add -l parameter:
```
ls -l

# Output
-rw------- 1 carol carol 539663 Dec 10 10:43 picture.jpg
```
Each column on the output above has a meaning. Let us have a look at the columns relevant for
this lesson.
• The first column on the listing shows the file type and permissions. For example, on drwxrwxrx:
◦ The first character, d, indicates the file type.
◦ The next three characters, rwx, indicate the permissions for the owner of the file, also
referred to as user or u.
◦ The next three characters, rwx, indicate the permissions of the group owning the file, also
referred to as g.
◦ The last three characters, r-x, indicate the permissions for anyone else, also known as
others or o.

The second column indicates the number of hard links pointing to that file. The fifth column shows
the filesize. The sixth column shows the date and time the file was last modified.

### What about directories
If you try to query information about a directory using ls -l, it will show you a listing of the
directory’s contents instead.
To avoid this and query information about the directory itself, add the -d parameter to ls: 
```
ls -l -d <directory>
```

### Viewing Hidden Files
On Linux, files whose name starts with a period (.) are automatically hidden. To see them we need to add the -a parameter to ls:
```
ls -la
```

	The directories . and .. however are special. . is a pointer to the current         directory. And .. is a pointer to the parent directory, the one which contains      the current one. In Linux, every directory contains at least these two              directories.

## Understanding Filetypes
We have already mentioned that the first letter in each output of ls -l describes the type of the
file. The three most common file types are:
```
- (normal file)
```
A file can contain data of any kind and help to manage this data. Files can be modified, moved,
copied and deleted.
```
d (directory)
```
A directory contains other files or directories and helps to organize the file system. Technically,
directories are a special kind of file.
```
l (symbolic link)
```
This “file” is a pointer to another file or directory elsewhere in the filesystem.
In addition to these, there are three other file types that you should at least know about, but are
out of scope for this lesson:
```
b (block device)
```
This file stands for a virtual or physical device, usually disks or other kinds of storage devices,
such as the first hard disk which might be represented by /dev/sda.
```
c (character device)
```
This file stands for a virtual or physical device. Terminals (like the main terminal on
/dev/ttyS0) and serial ports are common examples of character devices.
```
s (socket)
```
Sockets serve as “conduits” passing information between two programs.

## Understanding permissions
In the output of ls -l the file permissions are shown right after the filetype, as three groups of
three characters each, in the order r, w and x. Keep in mind that a dash - represents the lack of permission. 

### Permissions on Files
```
r
```
Stands for read and has an octal value of 4 (do not worry, we will discuss octals shortly). This
means permission to open a file and read its contents.
```
w
```
Stands for write and has an octal value of 2. This means permission to edit or delete a file.
```
x
```
Stands for execute and has an octal value of 1. This means that the file can be run as an
executable or script.

## Permissions on Directories

```
r
```
Stands for read and has an octal value of 4. This means permission to read the directory’s
contents, like filenames. **But it does not imply permission to read the files themselves.**
```
w
```
Stands for write and has an octal value of 2. This means permission to create or delete files in a
directory.
**Keep in mind that you cannot make these changes with write permissions alone, but also need**
**execute permission (x) to change to the directory.**
```
x
```
Stands for execute and has an octal value of 1. **This means permission to enter a directory, but**
**not to list its files (for that r is needed).**
Whenever someone tries to perform an action on the file, the permissions are checked in the same fashion.
First the system checks if the current user owns the file, and if this is true it applies the first set of
permissions only. Otherwise, it checks if the current user belongs to the group owning the file. In
that case, it applies the second set of permissions only. In any other case, the system will apply the
third set of permissions.

## Modifying File Permissions
The command chmod is used to modify the permissions for a file, and takes at least two parameters: the first one describes which permissions to change, and the second one points to the
file or directory where the change will be made. Keep in mind that only the owner of the file, or the system administrator (root) can change the permissions on a file.
The permissions to change can be described in two different ways, or "modes".
The first one, called symbolic mode offers fine grained control, allowing you to add or revoke a
single permission without modifying others on the set. The other mode, called octal mode, is easier
to remember and quicker to use if you wish to set all permission values at once.
Both modes lead to the same end result. So the command: 
```
chmod ug+rw-x,o-rwx text.txt

# and

chmod 660 text.txt

# will produce exactly the same output.
```

### Symbolic Mode
When describing which permissions to change in symbolic mode the first character(s) indicate(s)
whose permissions you will alter: the ones for the user (u), for the group (g), for others (o) and/or
for everyone (a).
Then you need to tell the command what to do: you can grant a permission (+), revoke a
permission (-), or set it to a specific value (=).
Of course, it's possible to modify multiple permissions at the same time. Separate them with a comma (,). 
Chmod also have a recursive mode. So, if we want to change the permissions for "all files inside a directories and its subdirectories" we can use -R parameter.

	Be careful and think twice before using the -R switch, as it is easy to change permissions on files and directories which you do not want to change, especially on directories with a large number of files and subdirectories.

### Octal Mode
In octal mode, the permissions are specified in a different way: as a three-digit value on octal
notation, a base-8 numeric system.
Each permission has a corresponding value, and they are specified in the following order: first
comes read (r), which is 4, then write (w), which is 2 and last is execute (x), represented by 1. If
there is no permission, use the value zero (0). So, a permission of rwx would be 7 (4+2+1) and r-x
would be 5 (4+0+1).
**If a permission value is odd, the file surely is executable!**

## Modifying File Ownership

The command chown is used to modify the ownership of a file or directory. The syntax is quite
simple:
```
chown USER:GROUPNAME FILENAME
```

Keep in mind that the user who owns a file does not need to belong to the group who owns a file. The user or group permission set can be omitted if you do not wish to change them.
Unless you are the system administrator (root), you cannot change ownership of a file to another
user or group you do not belong to. If you try to do this, you will get the error message Operation
not permitted.

## Querying Groups
To see which groups exist on your system, type #getent group.
If you want to know to which groups a user belongs, add the username as a parameter to groups:
```
groups carol
```
To do the reverse (see which users belong to a group) use groupmems. The parameter -g specifies
the group, and -l will list all of its members:
```
groupmems -g <groupname> -l
```
Notice that #groupmems can be run only as root.

## Default Permissions

Whenever we create a file or a directory, those will have default permissions. This permissions came from the *user mask* or #umask, which sets the default permissions for every file created. 
You can check the current value for umask:
```
umask

# Output
0022
```
This not look like symbolic or octal mode. we can add to the previous command the -S parameter:
```
umask -S

# Output
u=rwx,g=rx,o=rx
```
We can use umask to change the permissions for your current shell: 
```
umask u=rwx,g=rwx,o=
```
After run this command if we a directory, by default, it will have permission like:
```
drwxrwx---

# File do not get execute permissions

-rw-rw----
```

Below a table with every value and its respective meaning:
![[Pasted image 20250613093744.png]]

## Special Permissions
Besides the read, write and execute permissions for user, group and others, each file can have three other special permissions which can alter the way a directory works or how a program runs.

### Sticky Bit
The sticky bit, also called the restricted deletion flag, has the octal value 1 and in symbolic mode is
represented by a t within the other’s permissions. This applies only to directories, and has no effect on normal files. On Linux it prevents users from removing or renaming a file in a directory unless they own that file or directory.
Directories with the sticky bit set show a t replacing the x on the permissions for others on the
output of ls -l:
```
ls -ld Sample_Directory/
drwxr-xr-t 2 carol carol 4096 Dec 20 18:46 Sample_Directory/
```
In octal mode, the special permissions are specified using a 4-digit notation, with the first digit
representing the special permission to act upon.
For example, to set a the sticky bit (value 1) in octal mode with permissions 755, the command would be: 
```
chmod 1755 DIRECTORY

# Output
drwxr-xr-t 2 carol carol 4,0K Dec 20 18:46 Another_Directory
```

### Set GID
Set GID, also known as SGID or Set Group ID bit, has the octal value 2 and in symbolic mode is
represented by an s on the group permissions. This can be applied to executable files or
directories. On files, it will make the process run with the privileges of the group who owns the
file. When applied to directories, it will make every file or directory created under it inherit the
group from the parent directory.
Files and directories with SGID bit show an s replacing the x on the permissions for the group on
the output of ls -l:
```
ls -l test.sh
-rwxr-sr-x 1 carol root 33 Dec 11 10:36 test.sh
```

To add SGID permissions to a file in symbolic mode, the command would be:
```
chmod g+s test.sh
```

### Set UID
SUID, also known as Set User ID, has the octal value 4 and is represented by an s on the user
permissions in symbolic mode. It only applies to files and has no effect on directories. Its behavior
is similar to the SGID bit, but the process will run with the privileges of the user who owns the file.
You can combine multiple special permissions on one parameter. So, to set SGID (value 2) and
SUID (value 4) in octal mode for the script test.sh with permissions 755, you would type:
```
chmod 6755 FILENAME

# Output
-rwsr-sr-x 1 carol carol 66 Jan 18 17:29 test.sh
```


