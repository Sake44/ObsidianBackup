## BIOS or UEFI

The UEFI, short for Unified Extensible Firmware Interface, differs from BIOS in some key points. As
the BIOS, the UEFI is also a firmware, but it can identify partitions and read many filesystems
found in them. The UEFI does not rely on the #MBR(Master Boot Record), taking into account only the settings stored in
its non-volatile memory (NVRAM) attached to the motherboard.

UEFI works in this way: 

1. The POST (power-on self-test) process is executed to identify simple hardware failures as soon as the machine is powered on.
2. The UEFI activates the basic components to load the system, like video output, keyboard and
storage media.
3. UEFI’s firmware reads the definitions stored in NVRAM to execute the pre-defined EFI
application stored in the ESP partition’s filesystem. Usually, the pre-defined EFI application is a
bootloader.
4. If the pre-defined EFI application is a bootloader, it will load the kernel to start the operating
system.

### Bootloader

GRUB displays a list of operating systems available to boot.
Changing the kernel parameters is not usually required, but it can be useful to detect and solve operating system related problems. Kernel parameters must be added to the file
**/etc/default/grub** in the line GRUB_CMDLINE_LINUX to make them persistent across reboots.

## Initialization Inspection

The memory space where the kernel stores its messages, including the boot messages, is called the
kernel ring buffer. The messages are kept in the kernel ring buffer even when they are not
displayed during the initialization process, like when an animation is displayed instead.

The kernel ring buffer loses all messages when the system is turned off or we can run:
```
dmesg --clear
```

In systems based on systemd, command journalctl will show the initialization messages with
options **-b**, **--boot**, **-k** or **--dmesg**.
Previous initialization logs are also kept in systems based on #systemd, so messages from prior
operating system sessions can still be inspected. If options -b 0 or --boot=0 are provided, then
messages for the current boot will be shown. Options -b -1 or --boot=-1 will show messages
from the previous initialization.

A common feature among operating systems following Unix design principles is the employment
of separate processes to control distinct functions of the system. These processes, called #daemons (or, more generally, services), are also responsible for extended features underlying the operating system, like #network application services (HTTP server, file sharing, email, etc.), databases, ondemand configuration, etc. Although Linux utilizes a monolithic #kernel, many low level aspects of the operating system are affected by daemons, like load balancing and firewall configuration.

Services can be controlled by shell scripts or by a program and its supporting configuration files.

- The first method is implemented by the #SysVinit standard, also known as System V or just #SysV.
- The second method is implemented by #systemd and Upstart.

The service manager is the first program launched by the kernel during the boot process, so its #PID (process identification number) is always 1.

### SysVinit

A service manager based on the #SysVinit standard will provide predefined sets of system states,
called #runlevels, and their corresponding service script files to be executed. Runlevels are
numbered 0 to 6, being generally assigned to the following purposes:

**Runlevel 0**
System shutdown.
**Runlevel 1, s or single**
Single user mode, without network and other non-essential capabilities (maintenance mode).
**Runlevel 2, 3 or 4**
Multi-user mode. Users can log in by console or network. Runlevels 2 and 4 are not often used.
**Runlevel 5**
Multi-user mode. It is equivalent to 3, plus the graphical mode login.
**Runlevel 6**
System restart.

The program responsible for managing runlevels and associated daemons/resources is
**/sbin/init**. During system initialization, the #init program identifies the requested runlevel,
defined by a kernel parameter or in the **/etc/inittab** file.
Every runlevel may have many associated service files, usually scripts in the **/etc/init.d/** directory.
The syntax of the /etc/inittab file uses this format:
```
id:runlevels:action:process
```

The **id** is a generic name up to four characters in length used to identify the entry. The **runlevels**
entry is a list of runlevel numbers for which a specified action should be executed. The **action**
term defines how init will execute the process indicated by the term process. The available
actions are:

```
boot
```
The process will be executed during system initialization. The field runlevels is ignored.
```
bootwait
```
The process will be executed during system initialization and init will wait until it finishes to
continue. The field runlevels is ignored.
```
sysinit
```
The process will be executed after system initialization, regardless of runlevel. The field
runlevels is ignored.
```
wait
```
The process will be executed for the given runlevels and init will wait until it finishes to
continue.
```
respawn
```
The process will be restarted if it is terminated.
```
ctrlaltdel
```
The process will be executed when the init process receives the SIGINT signal, triggered when
the key sequence of Ctrl + Alt + Del is pressed.

The **telinit q** command should be executed every time after the #/etc/inittab file is modified.
The argument q (or Q) tells init to reload its configuration.
The command #runlevel shows the current runlevel for the system.
```
$ runlevel
N 3
```
The letter **N** in the output shows that the **runlevel** has not changed since last boot.

