
We have been learning to execute commands from the shell thus far, but we can also enter
commands into a file, and then set that file to be executable. When the file is executed, those commands are run one after the other. These executable files are called scripts, and they are an absolutely crucial tool for any Linux system administrator. Essentially, we can  consider Bash to be a programming language as well as a shell.

To create a script we can:

```
$ echo 'echo "Hello World!"' > new_script
$ cat new_script
echo "Hello World!"
```

To execute it we could:

```
./new_script
```

As we can see, we don't have enough permissions. 

```
$ ls -l new_script
-rw-rw-r-- 1 user user 20 Apr 30 12:12 new_script
```

We can see that the permissions for this file are set to 664 by default. We have not set this file to
have execute permissions yet.

```
$ chmod +x new_script
$ ls -l new_script
-rwxrwxr-x 1 user user 20 Apr 30 12:12 new_script
```

## Define the Interpreter

It is very good practice to specify the type of interpreter we want to use in the first line of a script.
This line is called a bang line or more commonly a shebang. It indicates to the system how we want this file to be executed.

```
#!/bin/bash
# This is our first comment. It is also good practice to document all scripts.
echo "Hello World!"
```

Let's see how to use [[OneNote/Notes/Linux/Turning commands into Script/Variable]] in script.
