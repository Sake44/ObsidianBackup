# Introduction

Every time we invoke a command, one or more processes are started. A well-trained system
administrator not only needs to create processes, but also be able to keep track of them and send them different types of signals if and when required. In this lesson we will look at job control and how to monitor processes.

## Job control

Jobs are processes that have been started interactively through a terminal, sent to the background and have not yet finished execution. We can find out about the active jobs in our linux system.

```bash
#!/bin/bash
jobs
```

### Job Specification

The jobs command as well as other utilities such as fg, bg and kill need a job specification (or #jobspec) to act upon a particular job.

Other job specifications are also possible: 

```bash
#!/bin/bash
%n
```
Job whose id number is n:

```bash 
#!/bin/bash
jobs %1

# Output 
[1]+ Stopped sleep 60
```

Jobs whose command line starts with str:

```bash 
#!/bin/bash
jobs %sl
```

Jobs whose command line contains str:

```bash
#!/bin/bash
jobs %?le
```

Current job: %+ or %%

```bash
#!/bin/bash
jobs %+
```

#### Job status: Suspension, Foreground and Background

Once a job is in the background or has been suspended, we can do any of three things to it:

```bash
#!/bin/bash
fg %1 
# fg moves the specified job to the foreground and makes it the current job.

# Or take it to the background

bg %1

# Or once in the background, the job can be brought back into the foreground with fg or killed
# Note the ampersand (&) meaning the job has been sent to the background.
sleep 100 &

# To terminate it:

kill %2 # %n = ID
```

#### Detached Jobs : nohup

The jobs we have seen in the previous sections were all attached to the session of the user who invoked them. That means that if the session is terminated, the jobs are gone. However, it is possible to #detach jobs from sessions and have them run even after the session is closed.

The syntax is as follows:

```bash
#!/bin/bash
nohup COMMAND &

# The & sends the process into the background
```

#### Process monitoring

A process or task is an instance of a running program. Thus, you create new processes every time you type in commands into the terminal.

The watch command executes a program periodically and allows us to watch the program's output change over time. 

```bash
#!/bin/bash
watch uptime

# To change the update interval for watch use the -n command plus the n of seconds
```

#### Sending signals to process: kill

Every single process has a unique process identifier (PID). TO find it, we can: 

```bash 
#!/bin/bash
pgrep <process name>

# Similar to pgrep (to find) we can use pkill (to kill it)
```

To kill multiple instance of the same process we can use **killall**

### top and ps

When it comes to process monitoring, two invaluable tools are top and ps. Whilst the **former** produces output **dynamically**, the **latter** does it **statically**. In any case, both are excellent utilities to have a comprehensive view of all processes in the system.

#### Interacting with top

To invoke top: 

```bash
#!/bin/bash
top
```

By default the output is sort by the percentage of CPU time used by each process. The behaviour can be modified by pressing the following keys within top: 

M
Sort by memory usage.
N
Sort by process ID number.
T
Sort by running time.
P
Sort by percentage of CPU usage.


#### ps 

To see all process with a terminal, type: 

```bash
#!/bin/bash
ps a
```
Concerning options, ps can accept three different styles: BSD, UNIX and GNU.

BSD: no dash required
UNIX: dash required
GNU: double dash required

