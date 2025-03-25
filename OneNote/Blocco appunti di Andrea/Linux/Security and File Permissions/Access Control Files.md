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

The following table lists the attributes stored in the file /etc/shadow, commonly referred to as
the “shadow file”.
The basic syntax for a line on this file is:
```
USERNAME:PASSWORD:LASTCHANGE:MINAGE:MAXAGE:WARN:INACTIVE:EXPDATE
```

Where:
#USERNAME
The username (same as /etc/passwd), like root, nobody, emma.
#PASSWORD
A one-way hash of the password, including preceding salt. For example: !!,
!$1$01234567$ABC…, $6$012345789ABCDEF$012….
#LASTCHANGE
Date of the last password change in days since the “epoch”, such as 17909.
#MINAGE
Minimum password age in days.
#MAXAGE
Maximum password age in days.
#WARN
Warning period before password expiration, in days.
#INACTIVE
Maximum password age past expiration, in days.
#EXPDATE
Date of password expiration, in days since the “epoch”.

### /etc/gshadow

/etc/gshadow is a file readable only by root and by users with root privileges that contains
encrypted passwords for groups, each on a separate line:

```
developer:$6$7QUIhUX1WdO6$H7kOYgsboLkDseFHpk04lwAtweSUQHipoxIgo83QNDxYtYwgmZTCU0qSCuCkErmyR2
63rvHiLctZVDR7Ya9Ai1::
```

Each line consists of four colon-delimited fields:
**Group name**
The name of the group.
**Encrypted password**
The encrypted password for the group (it is used when a user, who is not a member of the group, wants to join the group using the newgrp command — if the password starts with !, no
one is allowed to access the group with newgrp).
**Group administrators**
A comma-delimited list of the administrators of the group (they can change the password of the
group and can add or remove group members with the gpasswd command).
**Group members**
A comma-delimited list of the members of the group.
Now that we’ve seen where user and group information is stored, let’s talk about the most
important command-line tools to update these files.

## Adduser

To create a user:
```
useradd <username>
```

To delete user:

```
userdel <username>
```

To set a new password for user: 

```
passwd <username>
// need to be root
```

The most important options which apply to the useradd command are:
```
-c
```
Create a new user account with custom comments (for example full name).
```
-d
```
Create a new user account with a custom home directory.
```
-e
```
Create a new user account by setting a specific date on which it will be disabled.
```
-f
```
Create a new user account by setting the number of days after the password expires during
which the user should update the password.
```
-g
```
Create a new user account with a specific GID
```
-G
```
Create a new user account by adding it to multiple secondary groups.
```
-m
```
Create a new user account with its home directory.
```
-M
```
Create a new user account without its home directory.
```
-s
```
Create a new user account with a specific login shell.
```
-u
```
Create a new user account with a specific UID.