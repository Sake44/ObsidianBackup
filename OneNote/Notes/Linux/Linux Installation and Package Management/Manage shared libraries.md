### What's Shared Libraries

Also known as **shared objects**: pieces of compiled, reusable code like functions or classes, that are recurrently used by various programs.

Software libraries are collections of code that are intended
to be used by many different programs; just as physical libraries keep books and other resources to be used by many different people.

To build an **executable file** from a program’s source code, two important steps are necessary. First, the compiler turns the source code into machine code that is stored in so-called object files.
Secondly, the linker combines the object files and links them to libraries in order to generate the final executable file. This linking can be done statically or dynamically.

#### Static Libraries

A static library is merged with the program at link time. A copy of the library code is embedded into the program and becomes part of it. Thus, the program has no dependencies on the library at run time because the program already contains the libraries code. Having no dependencies can be seen as an advantage since you do not have to worry about making sure the used libraries are always available. On the downside, statically linked programs are heavier.

#### Shared libraries

In the case of shared libraries, the linker simply takes care that the program references libraries correctly. The linker does, however, not copy any library code into the program file.
At run time, though, the shared library must be available to satisfy the program’s
dependencies.

##### Shared Object File Naming Convention

The name of a shared library, also known as soname, follows a pattern which is made up of three elements:
    • Library name (normally prefixed by lib)
    • so (which stands for “shared object”)
    • Version number of the library
**Here an example: libpthread.so.0**

##### Common Location 

Common locations for shared libraries in a Linux system are:
• /lib
• /lib32
• /lib64
• /usr/lib
• /usr/local/lib

The library path is configured in the /etc directory, namely in the file /etc/ld.so.conf and, more common nowadays, in files residing in the **/etc/ld.so.conf.d** directory.

The /etc/ld.so.conf.d directory contains *.conf files:

```
$ ls /etc/ld.so.conf.d/
libc.conf x86_64-linux-gnu.conf
```

These *.conf files must include the absolute paths to the shared library directories:

```
$ cat /etc/ld.so.conf.d/x86_64-linux-gnu.conf
# Multiarch support
/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu
```

The #ldconfig command takes care of reading these config files:

```
$ sudo ldconfig -v
/usr/local/lib:
/lib/x86_64-linux-gnu:
libnss_myhostname.so.2 -> libnss_myhostname.so.2
libfuse.so.2 -> libfuse.so.2.9.7
libidn.so.11 -> libidn.so.11.6.16
libnss_mdns4.so.2 -> libnss_mdns4.so.2
libparted.so.2 -> libparted.so.2.0.1
(...)
```

#### Searching for the Dependencies of a Particular Executable

To look up the shared libraries required by a specific program, use the #ldd command followed by the absolute path to the program.

```
$ ldd /usr/bin/git
```


