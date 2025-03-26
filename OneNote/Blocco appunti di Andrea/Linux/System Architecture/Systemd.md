Currently, #systemd is the most widely used set of tools to manage system resources and services, which are referred to as units by **systemd**. A unit consists of a name, a type and a corresponding configuration file.

There are seven distinct types of systemd units:

```
service
```
The most common unit type, for active system resources that can be initiated, interrupted and
reloaded.
```
socket
```
The socket unit type can be a filesystem socket or a network socket. All socket units have a
corresponding service unit, loaded when the socket receives a request.
```
device
```
A device unit is associated with a hardware device identified by the kernel. A device will only
be taken as a systemd unit if a udev rule for this purpose exists. A device unit can be used to
resolve configuration dependencies when certain hardware is detected, given that properties
from the udev rule can be used as parameters for the device unit.
```
mount
```
A mount unit is a mount point definition in the filesystem, similar to an entry in /etc/fstab.
```
automount
```
An automount unit is also a mount point definition in the filesystem, but mounted
automatically. Every automount unit has a corresponding mount unit, which is initiated when
the automount mount point is accessed.
```
target
```
A target unit is a grouping of other units, managed as a single unit.

The main command for controlling systemd units is #systemctl. Command **systemctl** is used to
execute all tasks regarding unit activation, deactivation, execution, interruption, monitoring, etc.

To list all available units and shows if they are enabled to start when the system boots:

```
systemctl list-unit-files
```

## Upstart

The initialization scripts used by Upstart are located in the directory #/etc/init/. System services
can be listed with command **initctl list**.


## Shutdown and Restart

After #shutdown is executed, all processes receive the #SIGTERM signal, followed by the #SIGKILL signal, then the system shuts down or changes its runlevel.

The SysV implementation allows for the limiting of users that will be able to restart the machine
by pressing Ctrl + Alt + Del . This is possible by placing option -a for the shutdown command present at the line regarding ctrlaltdel in the **/etc/inittab** file. By doing this, only users whose
usernames are in the **/etc/shutdown.allow** file will be able to restart the system with the **Ctrl
+Alt + Del keystroke** combination.

