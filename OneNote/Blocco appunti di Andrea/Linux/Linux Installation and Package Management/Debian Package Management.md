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


