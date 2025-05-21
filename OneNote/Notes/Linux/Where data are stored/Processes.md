Every time a user issues a command, a program is run and one or more processes are generated.
Processes exist in a hierarchy. After the kernel is loaded in memory on boot, the first process is initiated which — in turn — starts other processes, which, again, can start other processes. Every #process has a unique identifier (PID) and parent process identifier (PPID). These are positive integers that are assigned in sequential order.

You can get a dynamic listing of all running processes with the **top** command.

Additional options: 

```
M
```
Sort by memory usage.
```
N
```
Sort by process ID number.
```
T
```
Sort by running time.
```
P
```
Sort by percentage of CPU usage.

### A Snapshot of Processes: ps

Another very useful command to get information about processes is ps. Whereas top provides dynamic information, that of **ps is static**.

The displayed information has to do with the process identifier (**PID**), the terminal in which the process is run (**TTY**), the CPU time taken by the process (**TIME**) and the command which started the process (**CMD**).
A useful switch for ps is #-f which shows the full-format listing.

### Process Information in the /proc Directory

#/proc includes a numbered subdirectory for every running process in the system (the number is the PID of the process)

Let's check how to monitor through logs our system. [[System Logging and System Messaging]]


