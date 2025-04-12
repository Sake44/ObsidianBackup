The Debian Package (dpkg) tool is the essential utility to install, configure, maintain and remove
software packages on Debian-based systems. The most basic operation is to install a .deb package,
which can be done with:

```
# dpkg -i PACKAGENAME
```

### Dealing with Dependencies

More often than not, a package may depend on others to work as intended. 

#dpkg will check if those dependencies are installed on your system, and will fail to install the
package if they are not. In this case, dpkg will list which packages are missing. However it cannot
solve dependencies by itself. It is up to the user to find the .deb packages with the corresponding
dependencies and install them.

### Removing Packages

To remove a package, pass the -r parameter to dpkg, followed by the package name.

```
dpkg -r unrar
```

You can pass multiple package names to dpkg -r, so they will all be removed at once.

### Getting package Information

To get information about a .deb package, such as its version, architecture, maintainer,
dependencies and more, use the dpkg command with the -I parameter, followed by the filename
of the package you want to inspect:

```
dpkg -I google-chrome-stable_current_amd64.deb
```

### Listing Installed Packages and Package Contents

To get a list of every package installed on your system, use the --get-selections option, as in
dpkg #--get-selections. You can also get a list of every file installed by a specific package by
passing the -L PACKAGENAME parameter to dpkg, like below:

```
dpkg -L unrar
```

#### Finding Out Which Package Owns a Specific File

Sometimes you may need to find out which package owns a specific file in your system. You can do so by using the #dpkg-query utility, followed by the -S parameter and the path to the file in question:

```
# dpkg-query -S /usr/bin/unrar-nonfree
```

Sometimes, due to a corrupt or malformed configuration file, you may wish to restore a package’s settings to its “fresh” state. Or you may wish to change the answers you gave to the initial configuration questions. To do this run the #dpkg-reconfigure utility, followed by the package name.

```
dkpg-reconfigure <package name>
```

#### Advanced Package Tool (apt)

The Advanced Package Tool (APT) is a package management system, including a set of tools, that greatly simplifies package installation, upgrade, removal and management. APT provides features like advanced search capabilities and automatic dependency resolution.
APT is not a “substitute” for dpkg.


There are many utilities that interact with APT, the main ones being:
```
apt-get
```
used to download, install, upgrade or remove packages from the system.
```
apt-cache
```
used to perform operations, like searches, in the package index.
```
apt-file
```
used for searching for files inside packages.

Before installing or upgrading software with APT, it is recommended to update the package index first in order to retrieve information about new and updated packages: 

```
apt-get update
```

Then to install and remove package we can:

```
apt-get install <package name>
```

```
apt-get remove <package name>
```
Be aware that when installing or removing packages, APT will do automatic **dependency**
**resolution**. This means that any additional packages needed by the package you are installing will also be installed, and that packages that depend on the package you are removing will also be removed.

Note that when a package is removed the corresponding configuration files are left on the system. To remove the config files we can use: 

```
apt-get purge <package name>

#or 

apt-get remove --purge <package name>
```

#### Fixing Broken Dependencies

It is possible to have “broken dependencies” on a system. This means that one or more of the installed packages depend on other packages that have not been installed, or are not present anymore.

#### Upgrading Packages

APT can be used to automatically upgrade any installed packages to the latest versions available from the repositories. This is done with the apt-get upgrade command. Before running it, first update the package index with apt-get update:

```
apt-get update

apt-get upgrade
```

We can also run them together with &&.

#### The Local Cache
When you install or update a package, the corresponding .deb file is downloaded to a local cache directory before the package is installed. By default, this directory is #/var/cache/apt/archives.

Partially downloaded files are copied to #/var/cache/apt/archives/partial/.

#### Searching for Packages

The apt-cache utility can be used to perform operations on the package index, such as searching for a specific package or listing which packages contain a specific file.
To conduct a search, use #apt-cache search followed by a search pattern.
```
# apt-cache search p7zip
```

#### The Sources List
APT uses a list of sources to know where to get packages from. This list is stored in the file
sources.list, located inside the #/etc/apt directory. This file can be edited directly with a text editor, like vi, pico or nano, or with graphical utilities like aptitude or synaptic.
A typical line inside **sources.list** looks like this:

```
deb http://us.archive.ubuntu.com/ubuntu/ disco main restricted universe multiverse
```

##### The /etc/apt/sources.list.d Directory

Inside the **/etc/apt/sources.list.d** directory you can add files with additional repositories to
be used by APT, without the need to modify the main /etc/apt/sources.list file.



