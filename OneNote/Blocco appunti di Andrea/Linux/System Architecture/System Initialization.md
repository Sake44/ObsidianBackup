The initialization of the operating system starts when the bootloader loads the kernel into RAM.
Then, the kernel will take charge of the CPU and will start to detect and setup the fundamental
aspects of the operating system, like basic hardware configuration and memory addressing.
The kernel will then open the initramfs (initial RAM filesystem). The initramfs is an archive
containing a filesystem used as a temporary root filesystem during the boot process.
As soon as the root filesystem is available, the kernel will mount all filesystems configured in
**/etc/fstab** and then will execute the first program, a utility named init. The init program is
responsible for running all initialization scripts and system daemons.