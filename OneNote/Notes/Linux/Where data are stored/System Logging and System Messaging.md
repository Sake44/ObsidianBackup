The logging daemon collects messages from other services and programs and stores them in log files, typically under **/var/log**.

When exploring log files, remember to be root (if you do not have reading permissions) and use a pager such as **less**;

Alternatively, you can use tail with the #-f switch to read the most recent messages of the file and dynamically show new lines as they are appended.

a few can contain binary data as is the case with **/var/log/wtmp** — which stores data relevant to successful logins. You can use the file command to determine which is the case:

```
$ file /var/log/wtmp
/var/log/wtmp: dBase III DBT, version number 0, next free block index 8
```

These files are normally read using special commands. #last is used to interpret the data in
**/var/log/wtmp**.


#### Log rotation

Log files can grow a lot over a few weeks or months and take up all free disk space. To tackle this, the utility #logrotate is used. It implements log rotation or cycling which implies actions such as moving log files to a new name, archiving and/or compressing them, sometimes emailing them to the sysadmin and eventually deleting them as they grow old.

#### Kernel Ring Buffer

The kernel ring buffer is a fixed-size data structure that records kernel boot messages as well as any live kernel messages. The function of this buffer — a very important one — is that of logging all the kernel messages produced on boot — when syslog is not yet available. The dmesg command prints the kernel ring buffer (which used to be also stored in /var/log/dmesg).
Because of the extension of the ring buffer, this command is normally used in combination with the text filtering utility grep or a pager such as less.

```
$ dmesg | grep boot
```

#### The System Journal: systemd-journald

#journalctl is the utility that is used to read and query systemd’s journal database. If invoked without options, it prints the entire journal. 
However, if invoked with the #-k or #--dmesg switches, it will be equivalent to using the **dmesg** command.

Other interesting options for journalctl include:
```
-b, --boot
```
It shows boot information.
```
-u
```
It shows messages about a specified unit. Roughly, a unit can be defined as any resource
handled by systemd. For example journalctl -u apache2.service is used to read
messages about the apache2 web server.
```
-f
```
It shows most recent journal messages and keeps printing new entries as they are appended to the journal — much like tail -f.