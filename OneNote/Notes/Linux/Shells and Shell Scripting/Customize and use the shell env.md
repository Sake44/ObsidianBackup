Think of variable as an imaginary box in which to temporarily place a piece of information. 
Bash classifies variables as either shell/local (those which live only within the limits of the shell in which they were created) or environment/global (those that are inherited by children shells and/or processes).

### Variables: Assignment and Reference
A variable can be defined as a name containing a value.
In Bash, giving a value to a name is called variable assignment and it is the way in which we create
or set variables. On the other hand, the process of accessing the value contained in the name is called variable referencing.
```
<variable name>=<variable name>
```
To reference to variable:
```
echo $<var name>
```

### Variable names
The name of a variable may contain letters (a-z,A-Z), numbers (0-9) and underscores (\_).
It may not start with a number or Bash will get confused
It may not contain spaces (not even using quotes)

### Variable Values
Concerning the reference or value of variables it is also important to consider a number of rules.
Variables may contain any alphanumerical characters (a-z,A-Z,0-9) as well as most other
characters (?,!,\*,.,/, etc.).
Variable values must be enclosed in quotes if they contain single spaces.
Variable values must also be enclosed in quotes if they contain such characters as those used for
redirection (<,>) or the pipe symbol (|).

However, single and double quotes are not always interchangeable. Depending on what we are
doing with a variable (assigning or referencing), the use of one or the other has implications and
will yield different results. In the context of variable assignment single quotes take all the
characters of the variable value literally, whereas double quotes allow for variable substitution:
```
$ lizard=uromastyx
$ animal='My $lizard'
$ echo $animal
My $lizard
$ animal="My $lizard"
$ echo $animal
My uromastyx
```

#### Local or Shell Variables
Local or shell variables exist only in the shell in which they are created. By convention, local
variables are written in lower-case letters.
In certain scenarios — such as when writing scripts — immutability can be an interesting feature
of variables. If we want our variables to be immutable, we can either create them readonly:
```
readonly reptile=tortoise
```
To list all readonly variable: 
```
readonly -p
```
A useful command when dealing with local variables is set.
set outputs all of the currently assigned shell variables and functions. Since that can be a lot of
lines (try it yourself!), it is recommended to use it in combination with a pager such as less:
```
set | less
```
A variable set in this way is a local variable, will not be inherited by any child processes spwned fom the current shell.
To unset a variable:
```
unset <var name>
```

#### Global or Environment Variables
Global or environment variables exist for the current shell as well as for all subsequent processes
spawned from it. By convention, environment variables are written in uppercase letters:
```
echo $SHELL
```
In order for a local shell variable to become an environment variable, the export command must
be used:
```
export reptile
```

#### Running a Program in a modified Environment
env can be used to modify the shell environment at a program’s time of execution.
To start a new Bash session with as empty an environment as possible — clearing most variables
(as well as functions and aliases) — we will use env with the -i option:
```
env -i bash
```
### Creating Aliases
An alias is a substitute name for another command(s). It can run like a regular command, but
instead executes another command according to the alias definition.
The syntax for declaring aliases is quite straightforward. Aliases are declared by writing the
keyword alias followed by the alias assignment.
```
alias alias-name=command(s)
```
The **unalias** command remove aliases
#### Expansion and Evaluation of Quotes in Aliases
When using quotes with environment variables, single quotes make the expansion dynamic:
```
$ alias where?='echo $PWD'
$ where?
/home/user2
$ cd Music
$ where?
/home/user2/Music
```
However, with double quotes the expansion is done statically

#### Persistence of Aliases: Startup Scripts
Just as with variables, for our aliases to gain persistence, we must put them into initialization
scripts that are sourced at startup. As we already know, a good file for users to put their personal
aliases in is ~/.bashrc.
If we notice, in ~/.bashrc, probably, there's three line like this:
```
# ~/.bash_aliases, instead of adding them here directly.
if [ -f ~/.bash_aliases ]; then
. ~/.bash_aliases
```
This function check for a file named .bash_aliases if it exists the it will be sourced. So, we can keep our aliases separated from other stuff. 

### Creating Functions
Compared to aliases, functions are more programmatic and flexible, specially when it comes to
exploiting the full potential of Bash special built-in variables and positional parameters. They are
also great to work with flow control structures such as loops or conditionals.
#### Two Syntaxes for Creating Functions
There are two valid syntaxes to define functions. 

##### Using the keyword function

On the one hand, we can use the keyword function, followed by the name of the function and
the commands between curly brackets:
```
function function_name {
command #1
command #2
command #3
...
command #n
}
```
##### Using ()
On the other, we can leave out the keyword function and use two brackets right after the
name of the function instead:
```
function_name() {
command #1
command #2
command #3
...
command #n
}
```
If we decide to skip line breaks and write a function in just one line, commands must be separated by semicolons.
Just as with variables and aliases, if we want functions to be persistent across system reboots we
have to put them into shell initialization scripts such as /etc/bash.bashrc (global) or
~/.bashrc (local).

#### Bash Special Built-in Variables
The Bourne Again Shell comes with a set of special variables which are particularly useful for
functions and scripts.
```
$?
```
This variable’s reference expands to the result of the last command run. A value of 0 means
success, every other value means error.
```
$$
```
It expands to the shell PID.
```
$!
```
It expands to the PID of the last background job.

##### Positional parameters $0 through $9

They expand to the parameters or arguments being passed to the function (alias or script) — $0
expanding to the name of the script or shell.
Example in the function below:
```
$ special_vars() {
> echo $0
> echo $1
> echo $2
> echo $3
>  }

# Run function:
$ special_vars debian ubuntu xorin
-bash
debian
ubuntu
zorin
```

```
$#
```
It expands to the number of arguments passed to the command.
```
$@, $*
```
They expand to the arguments passed to the command.
```
$_
```
It expands to the last parameter or the name of the script (amongst other things; see man bash
to find out more!):

#### Variables in Functions
Of course, variables can be used within functions.
To prove it, this time we will create a new empty file called funed and put the following function into it: 
```
editors() {
editor=emacs
echo "My editor is: $editor. $editor is a fun text editor."
}
```
Then source the file just created.
We can also use environment variables.
```
editors() {
editor=emacs
echo "The text editor of $USER is: $editor."
}
```
#### Positional parameter in functions
Something similar occurs with positional parameters.
We can pass them to functions from within the file or script (note the last line):
```
editors() {
editor=emacs
echo "The text editor of $USER is: $editor."
echo "Bash is not a $1 shell."
}
editors tortoise
```
#### Functions in Scripts
Functions are mostly found in Bash scripts.
We can change the previous function into a script:
```
#!/bin/bash

editors() {
editor=emacs
echo "The text editor of $USER is: $editor."
echo "Bash is not a $1 shell."
}
editors tortoise
```

We add only two lines: 
• The first line is the shebang and defines what program is going to interpret the script:
#!/bin/bash. Curiously enough, that program is bash itself.
• The last line is simply the invocation of the function.

Now we have to make the script executable:
```
chmod +x funed.sh
```
#### A Function within an Alias
We can put function into alias:
```
$ alias great_editor='gr8_ed() { echo $1 is a great text editor; unset -f gr8_ed; }; gr8_ed'
```
This long alias value deserves an explanation. Let us break it down:
• First there is the function itself: gr8_ed() { echo $1 is a great text editor; unset
-f gr8_ed; }
• The last command in the function — unset -f gr8_ed — unsets the function so that it does
not remain in the present bash session after the alias is called.
• Last but not least, to have a successful alias invocation, we must first invoke the function too:
gr8_ed.

As shown in unset -f gr8_ed above, the unset command is not only used to unset variables,
but also functions. In fact, there are specific switches or options:
```
unset -v
```
for variables
unset -f
for functions
If used without switches, unset will try to unset a variable first and — if it fails — then it will try to
unset a function.
#### A Function Within a Function
Now say we want to communicate two things to user2 every time she logs into the system:
• Say hello and recommend/praise a text editor.
• Since she is starting to put a lot of Matroska video files in its $HOME/Video folder, we also want
to give her a warning.
To accomplish that purpose, we have put the following two functions into /home/user2/.bashrc:
The first function (check_vids) does the checking on .mkv files and the warning:
```
check_vids() {
ls -1 ~/Video/*.mkv > /dev/null 2>&1
if [ "$?" = "0" ];then
echo -e "Remember, you must not keep more than 5 video files in your Video
folder.\nThanks."
else
echo -e "You do not have any videos in the Video folder. You can keep up to 5.\nThanks."
fi
}
```
check_vids does three things:
• It lists the mkv files in ~/Video sending the output — and any errors — to the so-called bitbucket
(/dev/null).
• It tests the output of the previous command for success.
• Depending on the result of the test, it echoes one of two messages.
The second function is a modified version of our editors function:

```
editors() {
editor=emacs
echo "Hi, $USER!"
echo "$editor is more than a text editor!"
check_vids
}
editors
```
It is important to observe two things:
• The last command of editors invokes check_vids so both functions get chained: The
greeting, praise and the checking and warning are executed in sequence.
• editors itself is the entry point to the sequence of functions so it is invoked in the last line
(editors).