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

