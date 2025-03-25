Security involves many concepts, one of the most common being the general concept of access controls. Before one can tackle file access controls such as ownership and permissions, one must understand the basic concepts of Linux user accounts, which are broken out into several types.

### Identifier
The User and Group Identifiers (UIDs/GIDs) are the basic, enumerated references to accounts. Early implementations were limited 16-bit (values 0 to 65535) integers, but 21st century systems support 64-bit UIDs and GIDs. Users and groups are enumerated independently, so the same ID can stand for both a user and group.
Every user has not only an UID, but also a primary GID. The primary GID for a user can be unique to that user alone, and may end up not being used by any other users. However, this group could also be a group shared by numerous users. In addition to these primary groups, each user can be member of other groups, too.

On Linux the superuser account is root, which always has UID 0. The superuser is sometimes called the system administrator, and has unlimited access and control over the system, including other users.
The default group for the superuser has the GID 0 and is also named root. The home directory for the superuser is a dedicated, top level directory, /root, only accessible by the root user himself.

### System Accounts

System accounts are typically pre-created at system installation time. These are for facilities, programs and services that will not run as the superuser. In an ideal world, these would all be operating system facilities.
The system accounts vary, but their attributes include:
• **UIDs are usually under 100 (2-digit) or 500-1000 (3-digit)**.
• Either no dedicated home directory or a directory that is usually not under /home.
• No valid login shell (typically /sbin/nologin), with rare exceptions.

### Service Accounts

Service accounts are typically created when services are installed and configured. Similar to
system accounts, these are for facilities, programs and services that will not run as the superuser.

- **UID/GID >1000 (4+ digit), but not a “standard” or “regular” user account, an account for services, with an UID/GID >1000 (4+ digits)**
