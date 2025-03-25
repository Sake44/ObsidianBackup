## BIOS or UEFI

The UEFI, short for Unified Extensible Firmware Interface, differs from BIOS in some key points. As
the BIOS, the UEFI is also a firmware, but it can identify partitions and read many filesystems
found in them. The UEFI does not rely on the MBR, taking into account only the settings stored in
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

