```
$ bzip2 bigfile2
$ gzip bigfile3
$ xz bigfile4
$ ls -lh
total 1.2M
-rw-r--r-- 1 emma emma 712K Jun 23 08:08 bigfile
-rw-r--r-- 1 emma emma 170K Jun 23 08:08 bigfile2.bz2
-rw-r--r-- 1 emma emma 179K Jun 23 08:08 bigfile3.gz
-rw-r--r-- 1 emma emma 144K Jun 23 08:08 bigfile4.xz
```

The tar program is probably the most widely used archiving tool on Linux systems.

```
$ tar cf archiving/3.1.tar compression
```

The **c** option instructs tar to create a new archive file and the **f** option is the name of the file to create. The argument immediately following the options is always going to be the name of the file to work on.

The tar program can also manage #compression and decompression of archives on the fly. tar does so by calling one of the compression tools discussed earlier in this section. It is as simple as adding the option appropriate to the compression algorithm. **The most commonly used ones are j, J, and z for bzip2, xz, and gzip, respectively.**

To see the content of an archive:

```
tar -tf <file .tar>
```



