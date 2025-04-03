When update-grub is run, GRUB 2 will scan for kernels and operating systems on the machine
and generate the corresponding menu entries on the /boot/grub/grub.cfg file. New entries can
be manually added to the script files within the /etc/grub.d directory.
These files should be executable, and are processed in numerical order by #update-grub.

Instead of directly specifying the device and partition you can also have GRUB 2 search for a file
system with a specific label or UUID (Universally Unique Identifier).

You can find the UUID of a filesystem with the command below:

```
ls -l /dev/disk/by-uuid/
```

When using the search command it is common to add the #--no-floppy parameter so GRUB will
not waste time searching on floppy disks.

Remember GRUB menu will not appear if #GRUB_TIMEOUT is set to 0 in
/etc/default/grub.

### Booting from rescue shell

In case of a boot failure GRUB 2 may load a #rescue shell, a simplified version of the shell we
mentioned before. You will recognize it by the command prompt, which displays as grub
rescue>.

After finding out which partition is the boot partition (with ls, as shown before), use the set
prefix= command, followed by the full path to the directory containing the GRUB 2 files. Usually
/boot/grub. In our example:

```
grub rescue> set prefix=(hd0,msdos1)/boot/grub
```

Now, load the modules normal and linux with the insmod command:

```
grub rescue> insmod normal
grub rescue> insmod linux
```



