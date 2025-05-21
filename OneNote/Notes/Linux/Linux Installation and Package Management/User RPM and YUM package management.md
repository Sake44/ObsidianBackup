The RPM Package Manager (rpm) is the essential tool for managing software packages on Red Hat-based (or derived) systems.

#### Installing, Upgrading and Removing **Packages**

```
# rpm -i PACKAGENAME
```

Where PACKAGENAME is the name of the .rpm package you wish to install.
If there is a previous version of a package on the system, you can upgrade to a newer version
using the -U parameter:
```
# rpm -U PACKAGENAME
```

In both operations you can add the #-v parameter to get a verbose output (more information is
shown during the installation) and #-h to get hash signs (#) printed as a visual aid to track
installation progress. Multiple parameters can be combined into one, so rpm -i -v -h is the
same as rpm #-ivh.

To remove an installed package, pass the #-e parameter (as in “erase”) to rpm, followed by the name of the package you wish to remove:
```
# rpm -e wget
```

rpm will check if those dependencies are installed on your system, and will fail to install the
package if they are not. In this case, rpm will list what is missing. **However it cannot solve**
**dependencies by itself.**

#### Listing Installed Packages

To get a list of all installed packages on your system, use the rpm #-qa (think of “query all”).

#### Getting Package Information
To get information about an installed package, such as its version number, architecture, install
date, packager, summary, etc., use rpm with the #-qi (think of “query info”) parameters, followed
by the package name.

```
# rpm -qi unzip
```
To get a list of what files are inside an installed package use the #-ql parameters:

```
# rpm -ql unzip
```

If you wish to get information or a file listing from a package that has not been installed yet, just
add the #-p parameter to the commands above, followed by the name of the RPM file (FILENAME).

```
# rpm -qip atom.x86_64.rpm
```

#### Finding Out Which Package Owns a Specific File

To find out which installed package owns a file, use the #-qf (think “query file”) followed by the
full path to the file:

```
# rpm -qf /usr/bin/unzip
```

#### YellowDog Updater Modified (YUM)
yum was originally developed as the Yellow Dog Updater (YUP), a tool for package management on the Yellow Dog Linux distribution. Over time, it evolved to manage packages on other RPM based systems, such as Fedora, CentOS, Red Hat Enterprise Linux and Oracle Linux.

### Searching for packages

In order to install a package, you need to know its name. For this you can perform a search with
yum search PATTERN, where PATTERN is the name of the package you are searching for.

```
yum search 7zip
```

#### Installing, Upgrading and Removing Packages

```
yum install <package name>
yum update <package name>
yum remove <package name>
```

If you omit the name of a package, you can update every package on the system for which an
update is available.

To see what packageprovides it, you can use yum whatprovides, followed by the name of the file you are searching for:
```
# yum whatprovides libgimpui-2.0.so.0
```

This also works for files already in your system.

####  Managing Software Repositories

For yum the “repos” are listed in the directory /etc/yum.repos.d/. Each repository is
represented by a .repo file.
To add a repository, use the #--add-repo parameter, followed by the URL to a .repo file.

```
# yum-config-manager --add-repo https://rpms.remirepo.net/enterprise/remi.repo
```

To get a list of all available repositories use yum repolist all. You will get an output similar to
this:

```
yum repolist all

# Output 

repo id          repo name  status
updates/7/x86_64 CentOS-7 - Updates enabled: 2,500
updates-source/7 CentOS-7 - Updates Sources disabled
```

disabled repositories will be ignored when installing or upgrading software. To enable or disable
a repository, use the #yum-config-manager utility, followed by the repository id.

**NOTE**
Yum stores downloaded packages and associated metadata in a cache directory (usually /var/cache/yum). As the system gets upgraded and new packages are installed, this cache can get quite large. To clean the cache and reclaim disk space you can use the yum clean command, followed by what to clean. The most useful parameters are packages (yum clean packages) to delete downloaded packages and metadata (yum clean metadata) to delete associated metadata. See the **manual page for yum** (type man yum) for more information.

#### DNF

dnf is the package management tool used on Fedora, and is a fork of yum.

**Searching for packages**

dnf search PATTERN, where PATTERN is what you are searching for. For example, dnf
search unzip will show all packages that contain the word unzip in the name or description.

**Getting information about a package**

dnf info PACKAGENAME

**Installing packages**

dnf install PACKAGENAME, where PACKAGENAME is the name of the package you wish to
install. You can find the name by performing a search.

**Removing packages**

dnf remove PACKAGENAME

**Upgrading packages**

dnf upgrade PACKAGENAME to update only one package. Omit the package name to upgrade all the packages in the system.

**Finding out which package provides a specific file**

dnf provides FILENAME

**Getting a list of all the packages installed in the system**

dnf list --installed

**Listing the contents of a package**

dnf repoquery -l PACKAGENAME

#### Managing Software Repositories

dnf works with software repositories (repos). Each distribution has a list of default repositories, and administrators can add or remove repos as needed.

To get a list of all available repositories, use dnf repolist. To list only enabled repositories, add
the #--enabled option, and to list only disabled repositories, add the #--disabled option.

```
dnf repolist
```


To add a repository, use dnf #config-manager #--add_repo URL, where URL is the full URL to
the repository. To enable a repository, use dnf config-manager --set-enabled REPO_ID.
Likewise, to disable a repository use dnf config-manager #--set-disabled REPO_ID. In both cases REPO_ID is the unique ID for the repository, which you can get using dnf repolist. Added repositories are enabled by default.
Repositories are stored in .repo files in the directory /etc/yum.repos.d/, with exactly the same
syntax used for yum.








