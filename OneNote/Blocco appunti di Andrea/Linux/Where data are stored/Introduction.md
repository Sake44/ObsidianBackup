Programs are distributed across a three-tier structure: the first tier (**/**) includes programs that can be necessary in single-user mode, the second tier (**/usr**) contains most multi-user programs and the third tier (**/usr/local**) is used to store software that is not provided by the distribution and has been compiled locally.

Typical locations for programs include:

```
/sbin
```
It contains essential binaries for system administration such as parted or ip.
```
/bin
```
It contains essential binaries for all users such as ls, mv, or mkdir.
```
/usr/sbin
```
It stores binaries for system administration such as **deluser**, or **groupadd**.
```
/usr/bin
```
It includes most executable files — such as **free, pstree, sudo or man** — that can be used by all users.
```
/usr/local/sbin
```
It is used to store locally installed programs for system administration that are not managed by the system’s package manager.
```
/usr/local/bin
```
It serves the same purpose as **/usr/local/sbin** but for regular user programs.

The **/opt** directory is sometimes used to store optional third-party applications.

We can find the location of programs with the #which command:
```
$ which git
/usr/bin/git
```

Let's check [[Etc Directory]].