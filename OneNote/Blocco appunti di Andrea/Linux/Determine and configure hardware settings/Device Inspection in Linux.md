When a hardware feature is not working as expected, it is important to identify where exactly the problem is happening. When a piece of hardware is not detected by the operating system, it is most likely that the part — or the port to
which it is connected — is defective. When the hardware part is correctly detected, but still does not properly work, there may be a problem on the operating system side.

### Commands for Inspection

The two essential commands to identify connected devices in a Linux system are:
```
lspci
```
Shows all devices currently connected to the PCI (Peripheral Component Interconnect) bus. PCI devices can be either a component attached to the motherboard, like a disk controller, or an expansion card fitted into a PCI slot, like an external graphics card.
```
lsusb
```
Lists USB (Universal Serial Bus) devices currently connected to the machine. Although USB
devices for almost any imaginable purpose exist, the USB interface is largely used to connect input devices — keyboards, pointing devices — and removable storage media.

Example of output for #lspci.
```
$ lspci
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)
04:02.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
04:04.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
04:0b.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
```
The hexadecimal numbers at the beginning of each line are the unique addresses of the corresponding PCI device. The command lspci shows more details about a specific device if its address is given with option **-s**, accompanied by the option **-v**.
Another way to verify which kernel module is in use for the specified device is provided by the option **-k**.
It is common to have a large set of loaded kernel modules in a standard Linux system at any time.The preferable way to interact with them is to use the commands provided by the kmod package,which is a set of tools to handle common tasks with Linux kernel modules like insert, remove, list,check properties, resolve dependencies and aliases. The lsmod command, for example, shows all currently loaded modules.
```
lsmod
```

Command modprobe can be used to both load and to unload kernel modules: to unload a module and its related modules, as long as they are not being used by a running process, command modprobe -r should be used.

```
modprobe -r snd-hda-intel
```

Customized parameters for a module can be made persistent by including them in
the file /etc/modprobe.conf or in individual files with the extension .conf in the directory
/etc/modprobe.d/.

Some of the important
files in /proc for inspecting hardware are:
```
/proc/cpuinfo
```
Lists detailed information about the CPU(s) found by the operating system.
```
/proc/interrupts
```
A list of numbers of the interrupts per IO device for each CPU.
```
/proc/ioports
```
Lists currently registered Input/Output port regions in use.
```
/proc/dma
```
Lists the registered DMA (direct memory access) channels in use.

