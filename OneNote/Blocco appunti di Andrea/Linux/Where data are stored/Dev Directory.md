The device directory /dev contains device files (or nodes) for all connected hardware devices.
These device files are used as an interface between the devices and the processes using them.

### Block devices
Are those in which data is read and written in blocks which can be individually addressed.
Examples include hard disks (and their partitions, like /dev/sda1), USB flash drives, CDs,
DVDs, etc.
### Character devices
Are those in which data is read and written sequentially one character at a time. Examples
include keyboards, the text console (/dev/console), serial ports (such as /dev/ttyS0 and so
on), etc.

Furthermore, /dev includes some special files which are quite useful for different programming
purposes:
```
/dev/zero
```
It provides as many null characters as requested.

```
/dev/null
```
Aka bit bucket. It discards all information sent to it.

```
/dev/urandom
```
It generates pseudo-random numbers.

Let's check the **/sys** Directory. [[Sys Directory]]