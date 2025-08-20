```
atime and noatime
```
By default, every time a file is read the access time information is updated. Disabling this (with
noatime) can speed up disk I/O. Do not confuse this with the modification time, which is
updated every time a file is written to.
```
auto and noauto
```
Whether the filesystem can (or can not) be mounted automatically with mount -a.
```
defaults
```
This will pass the options rw, suid, dev, exec, auto, nouser and async to mount.
```
dev and nodev
```
Whether character or block devices in the mounted filesystem should be interpreted.
```
exec and noexec
```
Allow or deny permission to execute binaries on the filesystem.
```
user and nouser
```
Allows (or not) an ordinary user to mount the filesystem.
```
group
```
Allows a user to mount the filesystem if the user belongs to the same group which owns the
device containing it.
```
owner
```
Allows a user to mount a filesystem if the user owns the device containing it.
```
suid and nosuid
```
Allow, or not, SETUID and SETGID bits to take effect.
```
ro and rw
```
Mount a filesystem as read-only or writable.
```
remount
```
This will attempt to remount an already mounted filesystem. This is not used on /etc/fstab,
but as a parameter to mount -o. For example, to remount the already mounted partition
/dev/sdb1 as read-only, you could use the command mount -o remount,ro /dev/sdb1.
When remounting, you do not need to specify the filesystem type, only the device name or the
mount point.
```
sync and async
```
Whether to do all I/O operations to the filesystem synchronously or asynchronously. async is
usually the default. The manual page for mount warns that using sync on media with a limited
number of write cycles (like flash drives or memory cards) may shorten the life span of the
device.