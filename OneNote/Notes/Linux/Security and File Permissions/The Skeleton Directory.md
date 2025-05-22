When you add a new user account, even creating its home directory, the newly created home
directory is populated with files and folders that are copied from the skeleton directory (by
default /etc/skel). The idea behind this is simple: a system administrator wants to add new
users having the same files and directories in their home. Therefore, if you want to customize the
files and folders that are created automatically in the home directory of the new user accounts,
you must add these new files and folders to the skeleton directory.