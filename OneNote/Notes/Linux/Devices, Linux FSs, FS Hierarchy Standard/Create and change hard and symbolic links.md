On Linux some files get a special treatment either because of the place they are stored in, such as
temporary files, or the way they interact with the filesystem, like links.

### Understanding links
As already mentioned, on Linux everything is treated as a file. But there is a special kind of file,
called a link, and there are two types of links on a Linux system:
##### Symbolic links
Also called soft links, they point to the path of another file. If you delete the file the link points
to (called target) the link will still exist, but it “stops working”, as it now points to “nothing”.
##### Hard links
Think of a hard link as a second name for the original file. They are not duplicates, but instead are an additional entry in the filesystem pointing to the same place (inode) on the disk.

### Working with Hard Links

The command to create a hard link on Linux is #ln. The basic syntax is:
```
ln TARGET LINKNAME
```
The TARGET must exist already (this is the file the link will point to), and if the target is not on the
current directory, or if you want to create the link elsewhere, you must specify the full path to it.

#### Managing Hard Links
Hard links are entries in the filesystem which have different names but point to the same data on
disk. All such names are equal and can be used to refer to a file. If you change the contents of one
of the names, the contents of all other names pointing to that file change since all these names
point to the very same data. If you delete one of the names, the other names will still work.
Note that every hard link pointing to a file increases the link count of the file. This is the number
right after the permissions on the output of ls -l.

#### Moving and removing Hard Links

Since hard links are treated as regular files, they can be deleted with rm and renamed or moved
around the filesystem with mv. And since a hard link points to the same inode of the target, it can
be moved around freely, without fear of “breaking” the link.

### Symbolic Links

The command to create a symbolic links is also ln, but with the -s parameter added: 
```
ln -s TARGET LINKNAME
```

As with hard links, you can omit the link name to create a link with the same name as the target in
the current directory.

#### Managing Symbolic Links
Symbolic links point to another path in the filesystem. You can create soft links to files and
directories, even on different partitions.
The first character on the permissions for the file is l, indicating a symbolic link. 

#### Moving and removing Symbolic links
Like hard links, symbolic links can be removed using rm and moved around or renamed using mv.
When creating symbolic links you should be aware that unless a path is fully specified the location
of the target is interpreted as relative to the location of the link. This may create problems if the
link, or the file it points to, is moved.
To avoid this always specify the full path to the target when creating the link. 