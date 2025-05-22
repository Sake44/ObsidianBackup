Typically, files will be created by the programs that work with the data stored in the files. An
empty file can be created using the touch command. If you run #touch on an existing file, the file’s contents won’t be changed, but the files modification timestamp will be updated.

To create a file:

```
touch <file name>
```

To list content of a file:

```
cat <file name>
```

To add characters to a file from command line we can:

```
echo hello > <file name>
```

The > character instructs the shell to write output of a command to the specified file instead of your terminal.

Let's see how to move files within our FS. (see [Move Files](Move%20Files.md))