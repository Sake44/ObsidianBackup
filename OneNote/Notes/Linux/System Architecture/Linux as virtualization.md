### Introduction

One of the great strengths of Linux is its versatility. One aspect of this versatility is the ability to use Linux as a means of hosting other operating systems, or individual applications, in a completely isolated and secure environment.

Virtualization is a technology that allows for a software platform, called a hypervisor, to run processes that contain a fully emulated computer system. The hypervisor is responsible for managing the physical hardware’s resources that can be used by individual virtual machines.

#### Types of virtual machines

There are three main types of virtual machines, the fully virtualized guest, the paravirtualized guest and the hybrid guest.

##### Fully virtualized

All instructions that a guest operating system is expected to execute must be able to run within a fully virtualized operating system installation.

In order for this type of virtualization to take place on x86 based hardware the Intel VT-x or AMD-V CPU extensions must be enabled on the system that has the hypervisor installed. This can be done from a BIOS or UEFI firmware configuration menu.

##### Paravirtualized

A paravirtualized guest (or PVM) is one where the guest operating system is aware that it is a running virtual machine instance. These types of guests will make use of a modified kernel and special drivers (known as guest drivers) that will help the guest operating system utilize software and hardware resources of the hypervisor.
Usually the performance of **paravirtualized VM** is better than fully virtualized guest due to the advantage that these software drivers provide. 

##### Hybrid

Paravirtualization and full virtualization can be combined to allow unmodified operating
systems to receive near native I/O performance by using paravirtualized drivers on fully
virtualized operating systems.

A virtual machine often consists of a group of files, primarily an XML file that defines
the virtual machine (such as its hardware configuration, network connectivity, display
capabilities, and more) and an associated hard disk image file that contains the installation of the operating system and its software.

#### Working with Virtual Machine Templates

Since virtual machines are typically just files running on a hypervisor, it is easy to create
templates that can be customized for particular deployment scenarios. Often a virtual machine
will have a basic operating system installation and some pre-configured authentication
configuration settings set up to ease future system launches.

#### The D-Bus Machine ID

Many Linux installations will utilize a machine identification number generated at install time,
called the D-Bus machine ID.
The following command can be used to validate that a D-Bus machine ID exists for the running
system:
```
dbus-uuidgen --ensure
```

The D-Bus machine ID is located at #/var/lib/dbus/machine-id and is symbolically linked to
#/etc/machine-id.
If two virtual machines do have the same D-Bus machine ID, follow the procedure below to generate a new one:
```
$ sudo rm -f /etc/machine-id
$ sudo dbus-uuidgen --ensure=/etc/machine-id
```

#### Securely Accessing Guests in the Cloud

The most prevalent method in use for accessing a remote virtual guest on a cloud platform is
through the use of OpenSSH software.

OpenSSH server running, while an administrator would use an OpenSSH client with pre-shared
keys for remote access.
An administrator would run the following command:
```
ssh-keygen
```

and follow the prompts to create a public and private #SSH key pair. The private key remains on
the administrator’s local system (stored in ~/.ssh/) and the public key gets copied to the remote
cloud system, the exact same method one would use when working with networked machines on
a corporate LAN.
The administrator would then run the following command:

```
ssh-copy-id -i <public_key> user@cloud_server
```

**Note that the permissions for SSH keys must be 0600 for a private key, and 0644 for a public key.**

#### Containers

Container technology is similar in some aspects to a virtual machine, where you get an isolated
environment to easily deploy an application. Whereas with a virtual machine an entire computer
is emulated, a container uses just enough software to run an application.
Containers make use of the control groups (better known as cgroups) mechanism within the Linux
kernel. The cgroup is a way to partition system resources such as memory, processor time as well
as disk and network bandwidth for an individual application. An administrator can use cgroups
directly to set system resource limits on an application, or a group of applications that could exist
within a single cgroup.


