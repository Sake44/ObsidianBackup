It’s possible that we want to verify all arguments that the user is entering. For example, perhaps
we want to ensure that all names passed to friendly2.sh contain only letters, and any special
characters or numbers will cause an error. To perform this error checking, we will use #grep.
```
$ echo 4n1ml | grep "^[A-Za-z]*$"
$ echo $?
1
```

The **^** and the **$** indicate the beginning and end of the line respectively. The [A-Za-z] indicates a
range of letters, upper or lower case. The * is a quantifier, and modifies our range of letters so that
we are matching zero to many letters. **In summary, our #grep will succeed if the input is only
letters, and fails otherwise.**
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
	 echo $username | grep "^[A-Za-z]*$" > /dev/null
 if [ $? -eq 1 ]
 then
	 echo "ERROR: Names must only contains letters."
exit 2
 else
	 echo "Hello $username!"
 fi
 done
 exit 0
 fi
```

We don’t want to see any output from the grep command, we only want to test its exit code,
which happens on **line 13**. Notice also that we are using an exit **code of 2** to indicate an invalid
argument. It is generally good practice to use different exit codes to indicate different errors.



