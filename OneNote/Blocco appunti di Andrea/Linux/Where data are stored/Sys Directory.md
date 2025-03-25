The sys filesystem (sysfs) is mounted on #/sys. It was introduced with the arrival of kernel 2.6 and meant a great improvement on **/proc/sys**.
Processes need to interact with the devices in /dev and so the kernel needs a directory which contains information about these hardware devices. This directory is /sys and its data is orderly arranged into categories. For instance, to check on the **MAC address** of your network card (**enp0s3**), you would cat the following file:

```
$ cat /sys/class/net/enp0s3/address
08:00:27:02:b2:74
```