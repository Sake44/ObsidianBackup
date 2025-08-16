Through the use of these two similar programs we can obtain specific types of shells:

**su**

Change user ID or become superuser (root). With this command we can invoke both login and
non-login shells:
• su - user2, su -l user2 or su --login user2 will start an interactive login shell as
user2.
• su user2 will start an interactive non-login shell as user2.
• su - root or su - will start an interactive login shell as root.
• su root or su will start an interactive non-login shell as root.

**sudo**

Execute commands as another user (including the supersuser). Because this command is
mainly used to gain root privileges temporarily, the user using it must be in the sudoers file.
To add users to sudoers we need to become root and then run:
```
usermod -aG sudo user2
```
We also can run an intercative shell as **sudo** user and go back to the previous user: 
```
sudo -i <some-command>
```
