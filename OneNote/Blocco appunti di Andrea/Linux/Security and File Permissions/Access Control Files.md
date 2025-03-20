Nearly all operating systems have a set of places used to store access controls. In Linux these are typically text files located under the /etc directory, which is where system configuration files should be stored. By default, this directory is readable by every user on the system, but writable only by root.

The main files related to user accounts, attributes and access control are:
```
/etc/passwd
```
This file stores basic information about the users on the system, including UID and GID, home directory, shell, etc. Despite the name, no passwords are stored here.
```
/etc/group
```
This file stores basic information about all user groups on the system, like group name and GID
and members.
```
/etc/shadow
```
This is where user passwords are stored. They are hashed, for security.
```
/etc/gshadow
```
This file stores more detailed information about groups, including a hashed password which
lets users temporarily become a member of the group, a list of users who can become a member of the group at and time and a list of group administrators.

```
/etc/sudoers
```
This file controls who can use the sudo command, and how.
```
/etc/sudoers.d
```
This directory may contain files that supplement the settings on the sudoers file.

### /etc/passwd

The typical syntax for a line on this file is:

```
USERNAME:PASSWORD:UID:GID:GECOS:HOMEDIR:SHELL
```

Where:
#USERNAME
The username aka login (name), like root, nobody, emma.

#PASSWORD
Legacy location of the password hash. Almost always x, indicating that the password is stored
in the file /etc/shadow.
#UID
User ID (UID), like 0, 99, 1024.
#GID
Default Group ID (GID), like 0, 99, 1024.
#GECOS
A CSV list of user information including name, location, phone number. For example: Emma
Smith,42 Douglas St,555.555.5555
#HOMEDIR
Path to the user’s home directory, like /root, /home/emma, etc.
#SHELL
The default shell for this user, like /bin/bash, /sbin/nologin, /bin/ksh, etc.

To change information of GECOS field, we can use:
```
chfn
```

### /etg/group

The /etc/group file contains fields always delimited by a colon (:), storing basic information
about the groups on the system.

```
NAME:PASSWORD:GID:MEMBERS
```

Where:
#NAME
is the group name, like root, users, emma, etc.
#PASSWORD
legacy location of an optional group password hash. Almost always x, indicating that the
password (if defined) is stored in the file /etc/gshadow.
#GID
Group ID (GID), like 0, 99, 1024.
#MEMBERS
a comma-separated list of usernames which are members of the group, like jsmith,emma.

### /etc/shadow
