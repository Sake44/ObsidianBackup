# Variable

When you start a new session from the terminal, the shell already sets some variables for you. The PATH variable is an example of this. We call these environment variables, because they usually define characteristics of our shell environment.

• Variable names must contain only alphanumeric characters or underscores, and are case sensitive. Username and username will be treated as separate variables.
• Variable substitution may also have the format ${username}, with the addition of the { }.
This is also acceptable.
• Variables in Bash have an implicit type, and are considered strings. This means that performing math functions in Bash is more complicated than it would be in other programming languages such as C/C++

### Using Quotes with variables

```
#!/bin/bash
# This is our first comment. It is also good practice to comment all scripts.
username=Carol Smith
echo "Hello $username!"
```

The interpreter interprets the space between Carol and Smith as the end of that assignment. So the command will not be found. To make it work we need to add #quotes. 

```
#!/bin/bash
# This is our first comment. It is also good practice to comment all scripts.
username="Carol Smith"
echo "Hello $username!"
```
One important thing to note in Bash is that double quotes and single quotes (') behave very differently. Double quotes are considered “weak”, because they allow the interpreter to perform substitution inside the quotes. Single quotes are considered “strong”, because they prevent any substitution from occurring.

### Returning the number of arguments

```
#!/bin/bash
# This is our first comment. It is also good practice to comment all scripts.
username=$1
echo "Hello $username!"
echo "Number of arguments: $#."
```

## Conditional Logic

Let's create a new script: 

```
#!/bin/bash
# A simple script to greet a single user.
if [ $# -eq 1 ]
then
username=$1
echo "Hello $username!"
else
echo "Please enter only one argument."
fi
echo "Number of arguments: $#."
```

Other comparison we can perform are: 
```
-ne
```
Not equal to
```
-gt
```
Greater than
```
-ge
```
Greater than or equal to
```
-lt
```
Less than
```
-le
```
Less than or equal to


Get a look to [[Best Practice]]. 