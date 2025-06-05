On any operating system, a disk needs to be partitioned before it can be used. A partition is a logical subset of the physical disk, and information about partitions are stored in a partition table.
Usually each partition is seen by an operating system as a separate “disk”, even if they all reside in
the same physical media. On Windows systems they are assigned letters like C: (historically the main disk), D: and so on. On Linux each partition is assigned to a directory under /dev, like
/dev/sda1 or /dev/sda2.

## Understanding MBR and GPT
