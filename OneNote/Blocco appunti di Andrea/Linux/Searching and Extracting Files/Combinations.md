The first combination that we will explore combines the redirection of the standard output and
standard error output to the same file. The **&>** and **&>>** operators are used, & representing the
combination of **channel 1** and **channel 2**. The first operator will overwrite the existing contents of
the file and the second one will append or add the new information at the end of the file.

```
$ find /usr admin &> newfile
$ cat newfile
/usr
/usr/share
/usr/share/misc
---------Omitted output----------
/usr/lib/libmagic.so.1.0.0
/usr/lib/libdns.so.81
/usr/games
find: `admin': No such file or directory
$ find /etc/calendar &>> newfile
$ cat newfile
/usr
/usr/share
/usr/share/misc
---------Omitted output----------
/usr/lib/libmagic.so.1.0.0
```

## Command Line Pipes

Redirection is mostly used to store the result of a command, to be processed by a different command. This type of intermediate process can become very tedious and complicated if you want the data to go through multiple processes. In order to avoid this, you can link the command directly via #pipes.

```
$ cat /etc/passwd | less
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
```

In other words, the first command’s output automatically becomes the second
command’s input.

It is possible to use multiple pipes at the same time. The intermediate commands that receive
input then change it and produce output are called filters. Let’s take the **ls -l** command and try
to count the number of words from the first 10 lines of the output. In order to do this, we will have
to use the head command that by default displays the first 10 lines of a file and then count the
words using the wc command:

```
$ ls -l | head | wc -w
10

// the -w option causes the command to only count the words within // the selected lines.

// -l, which specifies to the
// command to only count the lines, and -c, which is used to count // only the bytes.
```

Could be useful to use **-f** option with tail to look at last 10 lines of a file while it's being updated. 


## Commands used in this section

#cut
Removes sections from each line of a file.
#cat
Displays or concatenates files.
#find
Searches for files in a directory hierarchy.
#less
Displays a file, allowing the user to scroll one line at the time.
#more
Displays a file, a page at the time.
#head
Displays the first 10 lines of a file.
#tail
Displays the last 10 lines of a file.
#sort
Sorts files.
#wc
Counts by default the lines, words or bytes of a file.
