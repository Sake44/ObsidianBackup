Linux provides find to quickly search and locate files. find uses the following syntax:
```
find STARTING_PATH OPTIONS EXPRESSION
```

**STARTING_PATH**
defines the directory where the search begins.
**OPTIONS**
controls the behavior and adds specific criteria to optimize the search process.
**EXPRESSION**
defines the search query.
```
find . -name "myfile.txt"
```
The option #-name specifies that the search isì based on the name of the file. myfile.txt is the name of the file to search.

### Using Criteria to Speed search

Use #find to locate files based on type, size or time. By specifying one or more options, the desired results are obtained in less time.

Switches to finding files based on type include:
```
-type f
```
file search.
```
-type d
```
directory search.
```
-type l
```
symbolic link search.

Other criteria which could be used with find include:

```
-name
```
performs a search based on the given name.
```
-iname
```
searches based on the name, however, the case is not important (i.e. the test case myFile is
similar to MYFILE).
```
-not
```
returns those results that do not match the test case.
```
-maxdepth N
```
searches the current directory as well as subdirectories N levels deep.

##### Locating Files by Modification Time

find also allows to filter a directory hierarchy based on when the file was modified:

```
sudo find / -name ".conf" -mtime 7
```
This command would search for all files in the entire file system (the starting path is the root
directory, i.e. /) that end with the characters .conf and have been modified in the last seven days.

##### Locating files by size

find can also locate files by size. For example, searching for files larger than 2G in /var: 
```
sudo find /var -size +2G
```

#### Acting on the Result Set

Once a search is done, it is possible to perform an action on the resulting set by using -exec:
```
find . -name "*.conf" -exec chmod 644 '{}' \;
```
 

##### Using grep to Filter for Files Based on Content

```
$ find . -type f -exec grep "lpi" '{}' \; -print
```

This would search every object in the current directory hierarchy (.) that is a file (**-type f**) and
then executes the command grep "lpi" for every file that satisfies the conditions. The files that
match these conditions are printed on the screen (-print). The curly braces (**{}**) are a
placeholder for the find match results. The **{}** are enclosed in single quotes (**'**) to avoid passing
grep files with names containing special characters. The **-exec** command is terminated with a
semicolon (;), which should be escaped (\;) to avoid interpretation by the shell.
