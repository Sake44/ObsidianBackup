Think of a disk (or storage device, since modern devices do not contain any “disks” at all) as a
“physical container” for your data.
Before a disk can be used by a computer it needs to be #partitioned. A partition is a logical subset of the physical disk, like a logical “fence”.

Inside each partition there is a filesystem. The filesystem describes the way the information is
actually stored on the disk.
Partitions cannot span multiple disks. But using the **Logical Volume Manager (LVM)** multiple
partitions can be combined, even across disks, to form a single logical volume.

LVM is useful in situations where you would need to add more space to a partition
without having to migrate the data to a larger device.

## Mount Points

Before a filesystem can be accessed on Linux it needs to be mounted. This means attaching the
filesystem to a specific point in your system’s directory tree, called a #mount point.
When mounted, the contents of the #filesystem will be available under the mount point. For
example, imagine you have a partition with your users' personal data (their home directories),
containing the directories /john, /jack and /carol.

**/media**, which is now the default mount point for any userremovable
media (e.g. external disks, USB flash drives, memory card readers, optical disks, etc.)
connected to the system.

