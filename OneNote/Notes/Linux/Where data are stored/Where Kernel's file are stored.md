The Kernel resides in #/boot.
The /boot directory includes the following types of files, with names corresponding with the
respective kernel version:
**config-4.9.0-9-amd64**
Configuration settings for the kernel such as options and modules that were compiled along
with the kernel.

**initrd.img-4.9.0-9-amd64**
Initial RAM disk image that helps in the startup process by loading a temporary root filesystem into memory.

**System-map-4.9.0-9-amd64**
The System-map (on some systems it will be named System.map) file contains memory
address locations for kernel symbol names. Each time a kernel is rebuilt the file’s contents will change as the memory locations could be different. The kernel uses this file to lookup memory address locations for a particular kernel symbol, or vice-versa.

**vmlinuz-4.9.0-9-amd64**
The kernel proper in a self-extracting, space-saving, compressed format (hence the z in
vmlinuz; vm stands for virtual memory and started to be used when the kernel first got support for virtual memory).

**grub**
Configuration directory for the grub2 bootloader.


