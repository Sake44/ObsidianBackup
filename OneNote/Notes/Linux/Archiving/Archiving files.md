### The tar command (Archiving and Compression)

The #tar command, short for “tape archive(r)”, is used to create tar archives by converting a group of files into an archive.
```
tar [OPERATION_AND_OPTIONS] [ARCHIVE_NAME] [FILE_NAME(S)]
```
1. OPERATION

Only one operation argument is allowed and required. The most frequently used operations
are:
```
--create (-c)
```
Create a new tar archive.
```
--extract (-x)
```
Extract the entire archive or one or more files from an archive.
```
--list (-t)
```
Display a list of the files included in the archive.

2. OPTIONS
The most frequently used options are:
```
--verbose (-v)
```
Show the files being processed by the tar command.

```
--file=archive-name (-f archive-name)
```
Specifies the archive file name.

3. ARCHIVE_NAME
The name of the archive.

4. FILE_NAME(S)
A space-separated list of file names to be extracted. If not provided the entire archive is
extracted.

#### Creating an archive
```
tar -cvf NAME-OF-ARCHIVE.tar /PATH/TO/DIRECTORY-OR-FILE
```

**Tar works recursively.**

#### Extracting an Archive

```
tar -xvf archive.tar
```

To extract the contents of the archive to a specific directory we use -C:
```
tar -xvf archive.tar -C /tmp
```

#### The cpio command

#cpio stands for “copy in, copy out”. It is used to process archive files such as *.cpio or *.tar
files. 
cpio performs the following operations:
• Copying files to an archive.
• Extracting files from an archive.

```
ls | cpio -o > archive.cpio
```

To extract the archive we use: 

```
cpio -id < archive.cpio
```

##### The dd command

dd copies data from one location to another. The command line syntax of dd differs from many
other Unix programs, it uses the syntax option=value for its command line options rather than
the GNU standard -option value or --option=value formats:

```
dd if=oldfile of=newfile
```

if= is the input file and
of= refers to the output file.
