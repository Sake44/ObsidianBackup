The Linux shell environment allows the use of files — called scripts — containing commands from any available program in the system combined with shell builtin commands to automate a user’s and/or a system’s custom tasks. Indeed, many of the operating system maintenance tasks are performed by scripts consisting of sequences of commands, decision structures and conditional loops.
Scripts are nothing more than text files that behave like programs. An actual program — the interpreter — reads and executes the instructions listed in the script file. The interpreter can also start an interactive session where commands — including scripts — are read and executed as they are entered, as is the case with Linux shell sessions

### Script Structure and Execution
Basically, a script file is an ordered sequence of commands that must be executed by a corresponding command interpreter. How an interpreter reads a script file varies and there are distinct ways of doing so in a Bash shell session, but the default interpreter for a script file will be the one indicated in the first line of the script, just after the characters #! (known as *shebang*). By indicating this line, the interpreter for all the instructions will be /bin/bash. 
If yuo want to run the script without using bash command, you can give permission to that script, like:
```
chmod +x <script name>
```

### Variables
Variables in shell scripts behave in the same way as in interactive sessions, given that the interpreter is the same.
In addition to the ordinary variables created by the user, Bash scripts also have a set of special variables called parameters. Unlike ordinary variables, parameter names start with a non-alphabetical character that designates its function.
```
$*
```
All the arguments passed to the script.
```
$@
```
All the arguments passed to the script. If used with double quotes, as in "$@", every argument will be enclosed by double quotes.
```
$#
```
The number of arguments.
```
$0
```
The name of the script file.
```
$!
```
PID of the last executed program.
```
$$
```
PID of the current shell. 
```
$?
```
Numerical exit status code of the last finished command. For POSIX standard processes, a numerical value of 0 means that the last command was successfully executed, which also applies to shell scripts.
A positional parameter is a parameter denoted by one or more digits, other than the single digit 0.
For example, the variable $1 corresponds to the first argument given to the script (positional parameter one), $2 corresponds to the second argument, and so on. If the position of a parameter is greater than nine, it must be referenced with curly braces, as in ${10}, ${11}, etc.
