The initialization of the operating system starts when the bootloader loads the kernel into RAM.
Then, the kernel will take charge of the CPU and will start to detect and setup the fundamental
aspects of the operating system, like basic hardware configuration and memory addressing.
The kernel will then open the initramfs (initial RAM filesystem). The **initramfs** is an archive
containing a filesystem used as a temporary root filesystem during the boot process.
As soon as the root filesystem is available, the kernel will mount all filesystems configured in
**/etc/fstab** and then will execute the first program, a utility named init. The init program is
responsible for running all initialization scripts and system daemons.

## Boot Partition
On Linux the files necessary for the boot process are usually stored on a #boot partition, mounted under the root file system and colloquially referred to as /boot.

### Contents of the boot partition

#### Config File
This file, usually called config-VERSION (see example above), stores configuration parameters
for the Linux #kernel. This file is generated automatically when a new kernel is compiled or
installed and should not be directly modified by the user.
#### System map
This file is a look-up table matching symbol names (like variables or functions) to their
corresponding position in memory. This is useful when debugging a kind of system failure
known as a kernel panic, as it allows the user to know which variable or function was being
called when the failure occurred.
#### Linux kernel
This is the operating system kernel proper. The name is usually vmlinux-VERSION (e.g.
vmlinux-4.15.0-65-generic).
#### Initial RAM disk
This is usually called initrd.img-VERSION and contains a minimal root file system loaded
into a RAM disk, containing utilities and kernel modules needed so the kernel can mount the
real root filesystem.
#### Boot loader related files
On systems with GRUB installed, these are usually located on /boot/grub and include the
GRUB configuration file (/boot/grub/grub.cfg for GRUB 2 or /boot/grub/menu.lst in case
of GRUB Legacy), modules (in /boot/grub/i386-pc), translation files (in
/boot/grub/locale) and fonts (in /boot/grub/fonts).

Initial RAM disk
This is usually called initrd.img-VERSION and contains a minimal root file system loaded
into a RAM disk, containing utilities and kernel modules needed so the kernel can mount the
real root filesystem.
Boot loader related files
On systems with #GRUB installed, these are usually located on /boot/grub and include the
GRUB configuration file (/boot/grub/grub.cfg for GRUB 2 or /boot/grub/menu.lst in case
of GRUB Legacy), modules (in /boot/grub/i386-pc), translation files (in
/boot/grub/locale) and fonts (in /boot/grub/fonts).

### Grub 2

GRUB 2 can be installed using the grub-install utility.
The first disk on a system is usually the boot device and you may need to know whether there is a
boot partition on the disk. This can be done with the fdisk utility. To list all the partitions on the
first disk of your machine, use:

```
fdisk -l /dev/sda
```

Now, create a temporary directory under /mnt and mount the partition under it:

```
mkdir /mnt/tmp
mount /dev/sda1 /mnt/tmp
```

Then run grub-install, pointing it to the boot device (not the partition) and the directory where
the boot partition is mounted. If your system does have a dedicated boot partition, the command
is:

```
grub-install --boot-directory=/mnt/tmp /dev/sda
```

If you are installing to a system which does not have a boot partition, but just a /boot directory
on the root filesystem, point grub-install to it. So, the command is:

```
grub-install --boot-directory=/boot /dev/sda
```

### Configuring GRUB 2

The default configuration file for GRUB 2 is /boot/grub/grub.cfg. This file is automatically
generated and manual editing is not recommended. To make changes to the GRUB configuration,
you need to edit the file /etc/default/grub and then run the update-grub utility to generate a
compliant file.