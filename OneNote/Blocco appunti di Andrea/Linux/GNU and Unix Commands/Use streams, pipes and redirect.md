# Introduction

Operating systems inspired by Unix, like Linux, offer a great variety of input/output methods. In particular, the method of file descriptors allows to dynamically associate integer numbers with data channels, so that a process can reference them as its input/output data streams.

Standard Linux processes have three communication channels opened by default: the standard
input channel (most times simply called stdin), the standard output channel (stdout) and the
standard error channel (stderr).

## Redirect

The reassignment of a channel’s file descriptor in the shell environment is called a redirect. A redirect is defined by a special character within the command line. For example, to redirect the standard output of a process to a file, the greater than symbol > is positioned at the end of the command and followed by the path to the file that will receive the redirected output:

```
cat /proc/cpuinfo > /tmp/cpu.txt
```

To capture the content of #stderr, the redirect 2> should be used instead.

```
cat /proc/cpu_info 2> /tmp/error.txt
```

For example, a redirect to write both #stderr and #stdout to a file named log.txt can be written as >log.txt 2>&1.

To just discard the output of a command, its content can be redirected to the special file
/dev/null. For example, >log.txt 2>/dev/null saves the contents of stdout in the file
log.txt and discards the stderr.

Files are overwritten by output redirects unless Bash option noclobber is enabled, which can be done for the current session with the command set -o noclobber or set -C.

```
set -o noclobber
cat /proc/cpu_info 2>/tmp/error.txt

# Output
-bash: /tmp/error.txt: cannot overwrite existing file
```
To unset the noclobber option for the current session, run set +o noclobber or set +C.
Even with **noclobber** option enabled is possible to append a redirected data to existent content. This is accomplished with a redirection written with two greater than symbols >>:

The data source of the standard input of a process can be reassigned as well. The less than symbol < is used to redirect the content of a file to the stdin of a process.

```
uniq -c </tmp/error.txt
    2 cat: /proc/cpu_info: No such file or directory
```

### Here Document and Here String

Another way to redirect input involve the Here document and Here string methods. The Here
document redirect allows to type multi-line text that will be used as the redirected content. Two less than symbols << indicate a Here document redirect:

```
wc -c <<EOF
```

At the right of the two less than symbols << is the ending term EOF. The insertion mode will finish as soon as a line containing only the ending term is entered.

The Here string method is much like the Here document method, but for one line only:

```
wc -c <<<"How many characters in this Here String?"
```

#### Pipes

The vertical bar character |, also known as the pipe symbol, can be used to
create a pipeline connecting the output of a program directly into the input of another program, whereas command substitution allows to store the output of a program in a variable or use it directly as an argument to another command. 

The pipe character | tells the shell to start all distinct commands at the same time and to connect the output of the previous command to the input of the following command, left to right.

```
cat /proc/cpuinfo | wc
```

Pipes and redirects are exclusive, that is, one source can be mapped to only one target. Yet, it is possible to redirect an output to a file and still see it on the screen with program tee.

#### Command Substitution
