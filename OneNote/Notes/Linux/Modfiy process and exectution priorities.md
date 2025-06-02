# Introduction

Operating systems able to run more than one process at the same time are called multi-tasking or multi-processing systems. Whilst true simultaneity only happens when more than one processing unit is available, even single processor systems can mimic simultaneity by switching between processes very quickly.

Modern operating systems are also **preemptive**, that is, a running process can be put back in the queue so a more important process can control the CPU, even if the running process has not made a system call.

## The linux scheduler

Linux, as a preemptive multi-processing operating system, implements a scheduler that organizes the process queue. More precisely, the scheduler also decides which queued thread will be executed but process and thread are interchangeable in terms of context. (A process can branch out many independent thread). 

Every process has two predicates that intervene on its scheduling: **the scheduling policy and the scheduling priority.**
There are two main types of scheduling policies: **real-time policies and normal policies.** Processes under a real-time policy are scheduled by their priority values directly. If a more important process becomes ready to run, a less important running process is preempted and the higher priority process takes control of the CPU.
As a general purpose operating system, Linux runs just a few real-time processes. Most processes, including system and user programs, run under normal scheduling policies. Normal processes usually have the same priority value, but normal policies can define execution priority rules using another process predicate: the nice value.

### Reading Priorities
Linux reserves static priorities ranging from 0 to 99 for real-time processes and normal processes are assigned to static priorities ranging from 100 to 139, meaning that there are 39 different priority levels for normal processes. Lower values mean higher priority. The static priority of an active process can be found in the sched file, located in its respective directory inside the #/proc filesystem
```
grep ^prio /proc/1/sched
```
The priorities of all running process can be verified with the command ps -Al or ps -el:

```
ps -el
```
Due to historical reasons, priorities displayed by ps range from -40 to 99 by default, so the actual priority is obtained by adding 40 to it (in particular, 80 + 40 = 120).

It is also possible to continuously monitor processes currently being managed by the Linux kernel with program top. As with ps, top also displays the priority value differently. **To make it easier to identify real-time processes, top subtracts the priority value by 100, thus making all real-time priorities negative**, with a negative number or rt identifying them.

### Process Niceness
Every normal process begins with a default nice value of 0 (priority 120). The nice name comes from the idea that “nicer” processes allow other processes to run before them in a particular execution queue. Nice numbers range from -20 (less nice, high priority) to 19 (more nice, low priority). Linux also allows the ability to assign different nice values to threads within the same process. The NI column in ps output indicates the nice number.

It’s possible to start a process with a non-standard priority with the command nice. By default, nice changes the niceness to 10, but it can be specified with option -n:
```
nice -n 15 tar czf home_backup.tar.gz /home
```
The command **renice** can be used to change the priority of a running process. The option -p indicates the PID number of the target process.
```
renice -10 -p 2164
```
Besides renice, the priority of processes can be modified with other programs, like the program top. On the top main screen, the niceness of a process can be modified by pressing r and then the PID number of the process.