Compression is used to reduce the amount of space a specific set of data consumes. Compression is commonly used for reducing the amount of space that is needed to store a file. Another common use is to reduce the amount of data sent over a network connection.

Compression comes in two varieties, lossless and lossy. Things compressed with a lossless
algorithm can be decompressed back into their original form. Data compressed with a lossy
algorithm cannot be recovered.

The most common [Archiving Tools](Archiving%20Tools.md) for archiving files on Linux systems is tar. Most Linux distributions ship with the GNU version of tar, so it is the one that will be covered in this lesson. tar on its own only manages the archiving of files but does not compress them.
There are lots of compression tools available on Linux. Some common lossless ones are bzip2, gzip, and xz.

