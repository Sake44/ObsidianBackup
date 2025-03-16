The Linux command line redirects the information through specific standard channels. The standard input (stdin or channel 0) of the command is considered to be the keyboard and the standard output (stdout or channel 1) is considered the screen. There is also another channel that is meant to redirect error output (stderr or channel 2) of a command or a program’s error messages.

## I/O Redirection

I/O redirection enables the user to redirect information from or to a command by using a text file.

To redirect standard output to a file, instead of the screen, we need to use the **>** operator followed
by the name of the file. If the file doesn’t exist, a new one will be created, otherwise, the
information will overwrite the existing file.

```
$ echo "Hello World!" > text
$ cat text
Hello World!
```

If we want to add new information at the end of the file, we need to use the **>>** operator.

```
$ echo "Hello to you too!" >> text
$ cat text
Hello!
Hello to you too!
```

Let's see how to [Redirect Standard Error](Redirect%20Standard%20Error.md)
