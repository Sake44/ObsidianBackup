# Introduction

Operating systems able to run more than one process at the same time are called multi-tasking or multi-processing systems. Whilst true simultaneity only happens when more than one processing unit is available, even single processor systems can mimic simultaneity by switching between processes very quickly.

Modern operating systems are also **preemptive**, that is, a running process can be put back in the queue so a more important process can control the CPU, even if the running process has not made a system call.

## The linux scheduler

Linux, as a preemptive multi-processing operating system, implements a scheduler that organizes the process queue. More precisely, the scheduler also decides which queued thread will be executed but process and thread are interchangeable in terms of context. (A process can branch out many independent thread). 

