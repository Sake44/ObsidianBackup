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
