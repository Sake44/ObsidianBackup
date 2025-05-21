In the early days of Unix there was a folder for each type of data, such as /bin for binaries and **/boot** for the kernel(s). However, **/etc** (meaning et cetera) was created as a catch-all directory to store any files that did not belong in the other categories. Most of these files were configuration files. With the passing of time more and more configuration files were added so **/etc** became the main folder for configuration files of programs.

#group
System group database.
#hostname
Name of the host computer.
#hosts
List of IP addresses and their hostname translations.
#passwd
System user database — made up of seven fields separated by colons providing information
about the user.
#profile
System-wide configuration file for Bash.
#shadow
Encrypted file for user passwords.

• Initialization files ending in **rc**:
#bash.bashrc
System-wide **.bashrc** file for interactive bash shells.
#nanorc
Sample initialization file for GNU nano (a simple text editor that normally ships with any
distribution).
• Files ending in **.conf**:
#resolv.conf
Config file for the resolver — which provide access to the Internet Domain Name System
(DNS).
#sysctl.conf
Config file to set system variables for the kernel.

• Directories with the .d suffix:

Some programs with a unique config file (*.conf* or otherwise) have evolved to have a
dedicated *.d* directory which help build modular, more robust configurations.

In Debian — and Debian derivatives — such an approach has been applied to the list of reliable sources read by the package management tool apt: apart from the classic
**/etc/apt/sources.list**, now we find the **/etc/apt/sources.list.d** directory:

```
$ ls /etc/apt/sources*
/etc/apt/sources.list
/etc/apt/sources.list.d:
```