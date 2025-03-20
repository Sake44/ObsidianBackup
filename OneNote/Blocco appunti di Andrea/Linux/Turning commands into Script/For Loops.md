Let's take as example this variable:
```
FILES="/usr/sbin/accept /usr/sbin/pwck/ usr/sbin/chroot"
```

What we need is a way to “unpack” this variable and access each individual value, one after the other. To do this, we will use a structure called a for loop, which is present in all programming languages.

Full script:
```
#!/bin/bash
FILES="/usr/sbin/accept /usr/sbin/pwck/ usr/sbin/chroot"
for file in $FILES
do
ls -lh $file
done
```

The script that we can find in [[Handle Many Arguments]], now will look like this: 

```
 #!/bin/bash

 # a friendly script to greet users

 if [ $# -eq 0 ]
 then
 echo "Please enter at least one user to greet."
 exit 1
 else
 for username in $@
 do
 echo "Hello $username!"
 done
 exit 0
 fi
alias="
```

Remember that the variable that you define here can be named whatever you wish, and that all
the lines inside **do… done** will be executing once for each element of the array.

The output will look like this:
```
$ ./friendly2.sh Carol Dave Henry
Hello Carol!
Hello Dave!
Hello Henry!
```

If we want make our output seem a little more human, can do this:
```
1 #!/bin/bash
2
3 # a friendly script to greet users
4
5 if [ $# -eq 0 ]
6 then
7 echo "Please enter at least one user to greet."
8 exit 1
9 else
10 echo -n "Hello $1"
11 shift
12 for username in $@
13 do
14 echo -n ", and $username"
15 done
16 echo "!"
17 exit 0
18 fi
```

A couple of notes:
• Using -n with echo will suppress the newline after printing. This means that all echoes will
print to the same line, and the newline will be printed only after the !` on line 16.
• The shift command will remove the first element of our array.

We can use **regular expressions** also to [[Perform Error Checking]].