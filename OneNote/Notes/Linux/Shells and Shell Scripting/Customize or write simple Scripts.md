The Linux shell environment allows the use of files — called scripts — containing commands from
any available program in the system combined with shell builtin commands to automate a user’s
and/or a system’s custom tasks. Indeed, many of the operating system maintenance tasks are
performed by scripts consisting of sequences of commands, decision structures and conditional
loops.
Scripts are nothing more than text files that behave like programs. An actual program — the
interpreter — reads and executes the instructions listed in the script file. The interpreter can also
start an interactive session where commands — including scripts — are read and executed as they
are entered, as is the case with Linux shell sessions

### Script Structure and Execution
Basically, a script file is an ordered sequence of commands that must be executed by a
corresponding command interpreter. How an interpreter reads a script file varies and there are
distinct ways of doing so in a Bash shell session, but the default interpreter for a script file will be
the one indicated in the first line of the script, just after the characters #! (known as *shebang*). By indicating this line, the interpreter for all the instructions will be /bin/bash. 
If yuo want to run the script without using bash command, you can give permission to that script, like:
```
chmod +x <script name>
```
