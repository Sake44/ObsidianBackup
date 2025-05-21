
### Getting system information

To retrieve your current location in the file system, we can: 
```
pwd
```

To create a new file, we can use #touch 
```
touch newfile
```

and to list it: 

```
ls 
```

Besides your location in the filesystem, you will often want information about the Linux system
you are running. This might include the exact release number of your distribution or the Linux
kernel version that is currently loaded. The #uname tool is what you are after here. And, in
particular, uname using the #-a (“all”) option.
```
uname -a
```

### Getting Command Information

You will often come across documentation talking about Linux commands with which you are not
yet familiar. Perhaps the most useful information is found within the many
files of the man system. 
Typing #man followed by the name of a command will give you information that
includes the command name, a brief usage synopsis, a more detailed description, and some
important historical and licensing background.
```
man uname
```
#man only works when you give it an exact command name. If, however, you are not sure about the name of the command you are after, you can use the #apropos command to search through the man page names and descriptions. Assuming, for instance, that you cannot remember that it is
uname that will give you your current Linux kernel version, you can pass the word kernel to
apropros.

```
apropos kernel
```

If you do not need a command’s full documentation, you can quickly get basic data about a
command using #type.

```
type uname cp kill which
uname is hashed (/bin/uname)
cp is /bin/cp
kill is a shell builtin
which is /usr/bin/which
```

Notice that, besides being a regular binary command like cp, uname is also “hashed.” That is because user used recently #uname and to increase system efficiency, it was added to a hash table to make it more accessible the next time you run it.
**A quicker way to clean up the hash table is to run the command hash -d.**

The #which command will return the absolute path of a tool.

#### Using your command history
Typing #history will return the most recent commands you have executed with the most recent of
those appearing last. You can easily search through those commands by piping a specific string to
the #grep command.
```
history | grep bash_history
```

While the commands recenlty run are dynamically added to #history database the latest additions to your command history are not written to the .bash_history file until you exit your session.

Since every command in history database is related to a number, to rerun the same command you can:
```
!969 (number listed next to the command)
```
