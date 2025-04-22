## Introduction
Everything in Linux is a file, so knowing how to manipulate them is very important. 
A file is an entity that stores data and programs. It consists of content and meta data (file size, owner, creation date, permissions). Files are organized in directories. A directory is a file that stores other files.

### Manipulating Files

#### Using ls to List Files

The #ls command is one of the most important command line tools you should learn in order to
navigate the file system.

```
ls -l #long listing

# Example output

drwxr-xr-x 2 frank frank 4096 Apr 1 2018 Desktop
drwxr-xr-x 2 frank frank 4096 Apr 1 2018 Documents
drwxr-xr-x 2 frank frank 4096 Apr 1 2018 Downloads
-rw-r--r-- 1 frank frank 21 Sep 7 12:59 emp_name
-rw-r--r-- 1 frank frank 20 Sep 7 13:03 emp_salary
```

With -l, it shows file or directory permissions, owner, size, etc.
The first character in the output indicates the file type:
```
- # for a regular file.
d # for a directory.
c # for a special file
```

We can show the file sizes in an human readable format: 

```
ls -lh
#Example output

total 60K
drwxr-xr-x 2 frank frank 4.0K Apr 1 2018 Desktop
drwxr-xr-x 2 frank frank 4.0K Apr 1 2018 Documents
drwxr-xr-x 2 frank frank 4.0K Apr 1 2018 Downloads
```

To list all files including the hidden ones (those starting with .)

```
ls -a
```

#### Creating, Copying, Moving and Deleting Files

##### Creating files with touch
The touch command is the easiest way to create new, empty files. You can also use it to change
the timestamps (i.e., modification time) of existing files and directories. The syntax for using touch is:

```
touch OPTIONS <filename(s)>
```
Several touch options are specifically designed to allow the user to change the timestamps for
files. For example, the -a option changes only the access time, while the -m option changes only the modification time. The use of both options together changes the access and also the modification times to the current time:

```
touch -am <filename>
```

##### Copying files with cp

Basic syntaxt to copy a file
```
cp OPTIONS SOURCE DESTINATION
```

##### Moving files with mv

Just like cp for copying, Linux provides a command for moving and renaming files. It is called #mv.

```
mv <filename> DESTINATION_DIRECTORY
```

To rename a file, mv is used in the following way:

```
mv old_filename new_filename
```

By default, mv would not seek your confirmation (technically said “would not prompt”) if you wish to overwrite (rename) an existing file. However, you can allow the system to prompt, by using the option #-i. 

##### Deleting files with rm

```
rm file1

# request use information 

rm -i file1

# to force it

rm -f file1
```

#### Creating and Deleting Directories

##### Creating directories with mkdir

Creating directories is critical to organizing your files and folders. Files may be grouped together in a logical way by keeping them inside a directory. To create a directory, use mkdir:

```
mkdir OPTIONS DIRECTORY_NAME
```

To create a directory together with its subdirectories use the option #-p (“parents”):

```
mkdir -p parents/children
```

##### Removing directories with rmdir

rmdir deletes a directory if *it is empty*. Its syntax is given by:

```
rmdir OPTIONS DIRECTORY
```

You may remove a directory with its subdirectory: 

```
rmdir -p parents/children
```

#### Recursive manipulation of files and Directories

To manipulate a directory and its contents, you need to apply recursion. Recursion means, do an action and repeat that action all down the directory tree. In Linux, the options #-r or #-R or #--recursive are generally associated with recursion.

##### Recursive listing with ls -R

ls -R is used to list the contents of a directory together with its subdirectories and files.

##### Recursive copy with cp -r 

cp -r (or -R or --recursive) allows you to copy a directory together with its all subdirectories and files.

```
cp -r SOURCE DESTINATION
```

##### Recursive deletion with rm -r 

rm -r will remove a directory and all its contents (subdirectories and files).

### File globbing and wildcards

File globbing is a feature provided by the Unix/Linux shell to represent multiple filenames by
using special characters called wildcards. Wildcards are essentially symbols which may be used to substitute for one or more characters.

The following are some examples of file globbing:
```
rm *
# Delete all files in current working directory.

ls l?st
# List all files with names beginning with l followed by any single character and ending with st.

rmdir [a-z]*
# Remove all directories whose name starts with a letter.
```

#### Types of wildcards

```
There are three characters that can be used as wildcards in Linux:
* (asterisk)
# which represents zero, one or more occurrences of any character.

? (question mark)
# which represents a single occurrence of any character.
[ ] (bracketed characters)
# which represents any occurrence of the character(s) enclosed in the square brackets. It is
# possible to use different types of characters whether numbers, letters, other special characters. For example, the expression [0-9] matches all digits.
```

##### The asterisk 

An asterisk (*) matches zero, one or more occurrences of any character.
```
find /home -name *.png
# This would find all files that end with .png

cp -r animal/* forest

# all the contents of animal is copied into forest.
```

#### The question mark
The question mark matches a single occurence of a character

```
ls l?st.txt
# To return only the files that start with l followed by any single character and the characters st.txt, we use the question mark (?) wildcard
```

#### Bracketed Characters

The bracketed wildcards matches any occurrence of the character(s) enclosed in the square
brackets:

```
ls l[aef]st.txt
```

The square brackets can also take ranges:

```
ls l[a-z]st.txt
```

Multiple ranges could also be applied: 

```
ls student-[0-9][A-Z].txt
```
The listing shows a school directory with a list of registered students. To list only those students whose registration numbers meet the following criteria:
• begin with student-
• followed by a number, and an uppercase character
• and end with .txt

