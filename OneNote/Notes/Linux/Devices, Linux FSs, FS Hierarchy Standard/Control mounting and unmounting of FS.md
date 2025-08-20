Before a FS can be accessed on Linux, it needs to be mounted. 
This means attaching the filesystem to a specific point in your system’s directory tree, called a
mount point.
## Mounting and Unmounting FS
The command to manually mount a filesystem is called mount and its syntax is:
```
mount -t TYPE DEVICE MOUNTPOINT
```

Where: 
- TYPE: is the type of FS (ext2, btrfs, exfat, etc.)
- DEVICE: the name of the partition containing the filesystem
- MOUNTPOINT: where the filesystem will be mounted. 

```
mount -t exfat /dev/sdb1 ~/flash/
```

### Listing Mounted FSs
If you type just mount, you will get a list of all the filesystems currently mounted on your system.
To filter the output, you can use the -t parameter to list only filesystems of the corresponding type, like: 
```
mount -t ext4
```
The output in the examples above can be described in the format:
```
SOURCE on TARGET type TYPE OPTIONS
```

To unmount a filesystem, use the umount command, followed by the device name or the mount
point.
When unmounting a filesystem, you may encounter an error message stating that the target is
busy. This will happen if any files on the filesystem are open. However, it may not be immediately
obvious where an open file is located, or what is accessing the filesystem.
In such cases you may use the lsof command, followed by the name of the device containing the
filesystem, to see a list of processes accessing it and which files are open.

```
# umount /dev/sdb1
umount: /media/carol/External_Drive: target is busy.

# lsof /dev/sdb1
```
### Additional Command Line Parameters

```
-a
```
This will mount all filesystems listed in the file /etc/fstab (more on that in the next section).
```
-o or --options
```
This will pass a list of comma-separated mount options to the mount command, which can
change how the filesystem will be mounted. These will also be discussed alongside /etc/fstab.
```
-r or -ro

```
This will mount the filesystem as read-only.
```
-w or -rw
```
This will the mount filesystem as writable.

To unmount a filesystem, use the #unmount command.
Some of the command line parameters to umount are:
```
-a
```
This will unmount all filesystems listed in /etc/fstab.
```
-f
```
This will force the unmounting of a filesystem. This may be useful if you mounted a remote
filesystem that has become unreachable.
```
-r
```
If the filesystem cannot be unmounted, this will try to make it read-only.

### Dealing with Open Files
When unmounting a filesystem, you may encounter an error message stating that the target is
busy. This will happen if any files on the filesystem are open.

In such cases you may use the lsof command, followed by the name of the device containing the
filesystem, to see a list of processes accessing it and which files are open. For example:
```
# umount /dev/sdb1
umount: /media/carol/External_Drive: target is busy.
# lsof /dev/sdb1
COMMAND PID  USER  FD TYPE DEVICE SIZE/OFF NODE NAME
evince 3135 carol 16r  REG   8,17 21881768 5195 /media/carol/External_Drive/Documents/EBooks/
MagPi40.pdf
```

## Where to mount?
You can mount a filesystem anywhere you want. However, there are some good practices that
should be followed to make system administration easier.

Traditionally, /mnt was the directory under which all external devices would be mounted and a
number of pre-configured “anchor points” for common devices, like CD-ROM drives (/mnt/cdrom)
and floppy disks (/mnt/floppy) existed under it.
This has been superseded by /media, which is now the default mount point for any userremovable
media (e.g. external disks, USB flash drives, memory card readers, etc.) connected to the system.
That being said, whenever you need to manually mount a filesystem, it is good practice to mount it
under /mnt.

### Mounting FSs on Bootup
The file /etc/fstab contains descriptions about the filesystems that can be mounted. This is a
text file, where each line describes a filesystem to be mounted, with six fields per line in the
following order:
```
FILESYSTEM MOUNTPOINT TYPE OPTIONS DUMP PASS
```

Where:
```
FILESYSTEM
```
The device containing the filesystem to be mounted. Instead of the device, you can specify the
UUID or label of the partition, something which we will discuss later on.
```
MOUNTPOINT
```
Where the filesystem will be mounted.
```
TYPE
```
The filesystem type.
```
OPTIONS
```
Mount options that will be passed to mount.
```
DUMP
```
Indicates whether any ext2, ext3 or ext4 filesystems should be considered for backup by the
dump command. Usually it is zero, meaning they should be ignored.
```
PASS
```
When non-zero, defines the order in which the filesystems will be checked on bootup. Usually
it is zero.

For example, the first partition on the first disk of a machine could be described as:
```
/dev/sda1 / ext4 noatime,errors
```

The mount options on OPTIONS are a comma-separated list of parameters. The generics one we have: [[Generic mount options]].

## Using UUIDs and Labels
Specifying the name of the device containing the filesystem to mount may introduce some
problems. Sometimes the same device name may be assigned to another device depending on
when, or where, it was connected to your system. For example, a USB flash drive on /dev/sdb1
may be assigned to /dev/sdc1 if plugged on another port, or after another flash drive.
One way to avoid this is to specify the label or UUID (Universally Unique Identifier) of the volume.

The command lsblk can be used to query information about a filesystem and find out the label and UUID associated to it. To do this, use the -f parameter, followed by the device name:
```
lsblk -f <devicename>
```

Here is the meaning of each column:
```
NAME
```
Name of the device containing the filesystem.
```
FSTYPE
```
Filesystem type.
```
LABEL
```
Filesystem label.
```
UUID
```
Universally Unique Identifier (UUID) assigned to the filesystem.
```
FSAVAIL
```
How much space is available in the filesystem.
```
FSUSE%
```
Usage percentage of the filesystem.
```
MOUNTPOINT
```
Where the filesystem is mounted.

In /etc/fstab a device can be specified by its UUID with the UUID= option, followed by the UUID,
or with LABEL=, followed by the label:
```
UUID=6e2c12e3-472d-4bac-a257-c49ac07f3761 / ext4 noatime,errors
```
The same syntax can be used with the mount command. Instead of the device name, pass the UUID
or label.

## Mounting Disks with Systemd

Systemd is the init process, the first process to run on many linux distributions. Systemd is the init process, the first process to run on many Linux distributions. It is responsible for spawning other processes, starting services and bootstraping the system. Among many other tasks, systemd can also be used to manage the mounting (and automounting) of filesystems.

To use this feature of systemd, you need to create a config file called a *mount unit*. Each
volume to be mounted gets its own mount unit and they need to be placed in **/etc/systemd/system/**.
Mount units are simple text files with the .mount extension. The basic format is shown below:
```
[Unit]
# Short description of the mount unit, something like Mounts the backup disk.
Description=

[Mount]
# What should be mounted. The volume must be specified as /dev/disk/by-uuid/VOL_UUID where VOL_UUID is the UUID of the volume.
What=
# Should be the full path to where the volume should be mounted
Where=
# The filesystem type.
Type=
# Mount options that you may wish to pass, these are the same used with the mount command or in /etc/fstab.
Options=

[Install]
# Used for dependency management. In this case, we will use multi-user.target, which means that whenever the system boots into a multi-user environment (a normal boot) the unit will be mounted.
WantedBy=
```

But we are not done yet. To work correctly, the mount unit must have the same name as the
mount point. In this case, the mount point is /mnt/external, so the file should be named **mntexternal.mount**.
After that, you need to restart the systemd daemon with the systemctl command, and start the
unit:
```
systemctl daemon-reload
systemctl start mnt-external.mount
```

We can check the status of mounting with the command:
```
systemctl status mnt-external.mount
```
The systemctl start mnt-external.mount command will only enable the unit for the current session. If you want to enable it on every boot, replace start with enable:
```
systemctl enable mnt-external.mount
```

### Automonting a Mount Unit

Mount units can be automounted whenever the mount point is accessed. To do this, you need an
.automount file, alongside the .mount file describing the unit. The basic format is:
```
[Unit]
Description=

[Automount]
Where=

[Install]
WantedBy=multi-user.target
```
Save the file with the same name as the mount point (in this case, mnt-external.automount),
reload systemd and start the unit.
Now whenever the /mnt/external directory is accessed, the disk will be mounted. Like before, to
enable the automount on every boot you would use:
```
systemctl enable mnt-external.automount
```
