Basically, for a program to start running, it has to be loaded into memory. By and large, when we speak of memory we refer to **Random Access Memory (RAM)** and — when compared to mechanical hard disks — it has the advantage of being a lot faster. On the down side, it is volatile.

### Physical Memory

Also known as RAM, it comes in the form of chips made up of integrated circuits containing
millions of transistors and capacitors.

### Swap
Also known as swap space, it is the portion of virtual memory that lives on the hard disk and is used when there is no more #RAM available.

To check for #free memory (command: **free**) parses /proc/meminfo and displays the amount of free and used memory in the system in a very clear manner:

Let us explain the different columns:
#total
Total amount of physical and swap memory installed.
#used
Amount of physical and swap memory currently in use.
#free
Amount of physical and swap memory currently not in use.
#shared
Amount of physical memory used — mostly — by tmpfs.
#buff/cache
Amount of physical memory currently in use by kernel buffers and the page cache and slabs.
#available
Estimate of how much physical memory is available for new processes.
By default free shows values in kibibytes, but allows for a variety of switches to display its results in different units of measurement. Some of these options include:
#-b
Bytes.
#-m
Mebibytes.
#-g
Gibibytes.
#-h
Human-readable format.