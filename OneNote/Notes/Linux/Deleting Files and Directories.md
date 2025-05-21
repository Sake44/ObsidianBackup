The rm command can #delete files and directories, while the rmdir command can only delete
directories.

```
rm <file name>
```

By default, #rmdir refuses to delete a directory that is not empty. Use rmdir to remove one of the empty sub directories of the deleting directory:

```
rm -r < directory name>
```

By default, rm only works on regular files. The -r option is used to
override this behavior. Be careful, rm -r is an excellent foot gun! When you use the -r option, rm will not only delete any directories, but everything within that directory, including sub directories and their contents.

Let's see how to copy files. (See [Copying Files and Directories](Copying%20Files%20and%20Directories.md))
