Zypper is the package management tool used on SUSE Linux and OpenSUSE. Feature-wise it is similar to apt and yum, being able to install, update and remove packages from a system. 

#### Updating the Package index

Like other package management tools, zypper works with repositories containing packages and metadata.

```
zypper refresh
```

#### Searching for packages

To search for a package, use the search (or se) operator, followed by the package name:

```
zypper se gnumeric
```

The search operator can also be used to list all the installed packages. Use **-i** parameter. 

#### Installing, Upgrading and Removing Packages


To install a software package, use the install (or in) operator, followed by the package name.

```
zypper in <package name>
```

zypper can also be used to install an RPM package on disk, while trying to satisfy its dependencies using packages from the repositories. To do so, just provide the full path to the package instead of a package name, like **zypper in /home/john/newpackage.rpm.**

To remove a package, use the remove (or rm) operator, followed by the package name:

```
zypper rm <package name>
```

Keep in mind that removing a package also removes any other packages that depend on it.

#### Finding Which Packages Contain a Specific File

To see which packages contain a specific file, use the search operator followed by the --provides
parameter and the name of the file. 

#### Getting package information

To see the metadata associated with a package, use the info operator followed by the package name.

#### Managing Software repositories

zypper can also be used to manage software repositories. To see a list of all the repositories
currently registered in your system, use zypper repos.

