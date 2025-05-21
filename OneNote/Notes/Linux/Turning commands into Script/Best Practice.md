# Best Practice

* All scripts should begin with a shebang, which defines the path to the interpreter.
* All scripts should include comments to describe their use.
* This particular script works with an argument, which is passed to the script when it is called.
* This script contains an if statement, which tests the conditions of a built-in variable $#. This
variable is set to the number of arguments.
* If the number of arguments passed to the script equals 1, then the value of the first argument is
passed to a new variable called username and the script echoes a greeting to the user.
Otherwise, an error message is displayed.
* Finally, the script echoes the number of arguments. This is useful for debugging.

### How **cat** works

The explanation for this behaviour is this: any execution of the cat utility will return an exit code.
An exit code will tell us if the command succeeded, or experienced an error. An exit code of zero indicates that the command completed successfully. This is true for almost every Linux command ./ethat you work with.

```

#!/bin/bash

# A simple script to greet a single user.

if [ $# -eq 1 ]
then

username=$1

echo "Hello $username!"
exit 0

else
echo "Please enter only one argument."
exit 1
fi

echo "Number of arguments: $#."
```

Notice that the echo command on line 15 was ignored entirely. Using exit will end the script
immediately, so this line is never encountered.

Let's check how to [[Handle Many Arguments]].

