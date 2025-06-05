Regular expressions consist of character sequences that make up a generic pattern used to locate and sometimes modify a corresponding sequence in a larger string of characters. Regular expressions greatly expand the ability to: #REs

	• Write parsing rules to requests in HTTP servers, nginx in particular.
	• Write scripts that convert text-based datasets to another format.
	• Search for occurrences of interest in journal entries or documents.
	• Filter markup documents, keeping semantic content.

The simplest regular expression contains at least one **atom**. An atom, so named because it’s the basic element of a regular expression, is just a character that may or may not have special meaning:
```
. (dot)
Atom matches with any character.

^ (caret)
Atom matches with the beginning of the line

$ (dollar sign)
Atom matches with the end of the line
```

## Bracket expression

There is another type of atom named bracket expression. Although not a single character, brackets [] (including their content) are considered a single atom. A bracket expression usually is just a list of literal characters enclosed by [], making the atom match any single character from the list. For example, the expression [1b] can be found in both strings abcd and a1cd. To specify characters the atom should not correspond to, the list must begin with ^, as in [^1b].
Bracket expression lists also accept classes instead of just single characters and ranges. Traditional character classes are:
```
[:alnum:]
```
Represents an alphanumeric character.
```
[:alpha:]
```
Represents an alphabetic character.
```
[:ascii:]
```
Represents a character that fits into the ASCII character set.
```
[:blank:]
```
Represents a blank character, that is, a space or a tab.
```
[:cntrl:]
```
Represents a control character.
```
[:digit:]
```
Represents a digit (0 through 9).
```
[:graph:]
```
Represents any printable character except space.
```
[:lower:]
```
Represents a lowercase character.
```
[:print:]
```
Represents any printable character including space.
```
[:punct:]
```
Represents any printable character which is not a space or an alphanumeric character.
```
[:space:]
```
Represents white-space characters: space, form-feed (\f), newline (\n), carriage return (\r),
horizontal tab (\t), and vertical tab (\v).
```
[:upper:]
```
Represents an uppercase letter.
```
[:xdigit:]
```
Represents hexadecimal digits (0 through F).

### Quantifiers
The reach of an atom, either a single character atom or a bracket atom, can be adjusted using an
atom quantifier. Atom quantifiers define atom sequences, that is, matches occur when acontiguous repetition for the atom is found in the string.
The * quantifier has the same function in both basic and extended REs (atom occurs zero or more
times) and it’s a literal character if it appears at the beginning of the regular expression or if it’s
preceded by a backslash \.

### Bounds
A bound is an atom quantifier that, as the name implies, allows a user to specify precise quantity boundaries for an atom. In extended regular expressions, a bound may appear in three forms:

```
{i}

The atom must appear exactly i times (i an integer number). For example, [[:blank:]]{2} matches with exactly two blank characters.

{i,}
The atom must appear at least i times (i an integer number). For example, [[:blank:]]{2,} matches with any sequence of two or more blank characters.

{i,j}
The atom must appear at least i times and at most j times (i and j integer numbers, j greater then i). For example, xyz{2,4} matches the xy string followed by two to four of the z character.
```

### Branches and Back References
An extented regular expression can be divided into *branches*, each one an indipendent regular expression. Branches are separated by | and the combined regular expression will match anything that corresponds to any of the branches. 
An extended regular expression enclosed in () can be used in a back reference. For example,
```
([[:digit:]])\1
```
 will match any regular expression that repeats itself at least once, because the
\1 in the expression is the back reference to the piece matched by the first parenthesized
subexpression. If more than one parenthesized subexpression exist in the regular expression, they
can be referenced with \2, \3 and so on.

### Searching with Regular Expressions
The immediate benefit offered by regular expressions is to improve searches on filesystems and in
text documents. The -regex option of command find allows to test every path in a directory hierarchy against a regular expression. For example,
```
find $HOME -regex '.*/\..*'
```

searches for files greater than 100 megabytes (100 units of 1048576 bytes), but only in paths inside
the user’s home directory that do contain a match with .*/\..*, that is, a /. surrounded by any other number of characters. In other words, only hidden files or files inside hidden directories will be listed, regardless of the position of /. in the corresponding path.

## The pattern finder and stream editor
Regular expressions are an important technique used not only in system administration, but also in data mining and related areas. Two commands are specially suited to manipulate files and text data using regular expressions: **grep and sed**.

### Grep
One of the most common uses of grep is to facilitate the inspection of long files, using the regular
expression as a filter applied to each line. It can be used to show only the lines starting with a certain term.

```
grep '^options' /etc/modprobe.d/alsa-base.conf

# Listing only option line
```

The pipe | character can be employed to redirect the output of a command directly to grep's
input. The following example uses a bracket expression to select lines from fdisk -l output, starting with Disk /dev/sda or Disk /dev/sdb:
```
fdisk -l | grep '^Disk /dev/sd[ab]'
```

Option #-c or #--count tells grep to show how many lines had matches.
The option can be placed before or after the regular expression. Other important #grep options are: 

```
-c or --count
```
Instead of displaying the search results, only display the total count for how many times a
match occurs in any given file.
```
-i or --ignore-case
```
Turn the search case-insensitive.
```
-f FILE or --file=FILE
```
Indicate a file containing the regular expression to use.
```
-n or --line-number
```
Show the number of the line.
```
-v or --invert-match
```
Select every line, except those containing matches.
```
-H or --with-filename
```
Print also the name of the file containing the line.
```
-z or --null-data
```
Rather than have grep treat input and output data streams as separate lines (using the newline
by default) instead take the input or output as a sequence of lines. When combining output
from the find command using its -print0 option with the grep command, the -z or --null
-data option should be used to process the stream in the same manner.

Although activated by default when multiple file paths are given as input, the option -H is not
activated for single files. That may be critical in special situations, like when grep is called directly by find, for instance:

```
find /usr/share/doc -type f -exec grep -i '3d modeling' "{}" \; | cut -c -100
```
In this example, find lists every file under /usr/share/doc then passes each one to grep, which
in turn performs a case-insensitive search for 3d modeling inside the file. The pipe to cut is there just to limit output length to 100 columns. Note, however, that there is no way of knowing from which file the lines came from. This issue is solved by adding -H to grep:
```
find /usr/share/doc -type f -exec grep -i -H '3d modeling' "{}" \; | cut -c -100
```
To make the listing even more informative, leading and trailing lines can be added to lines with matches.
The option -1 instructs grep to include one line before and one line after when it finds a line with
a match.

There are two complementary programs to grep: egrep and fgrep. The program egrep is equivalent to the command grep -E, which incorporates extra features other than the basic regular expressions. For example, with egrep it is possible to use extended regular expression features, like branching:

```
find /usr/share/doc -type f -exec egrep -i -H -1 '3d (modeling|printing)' "{}" \; | cut -c -100
```
The program fgrep is equivalent to grep -F, that is, it does not parse regular expressions. It is useful in simple searches where the goal is to match a literal expression.

### Sed
The purpose of the sed program is to modify text-based data in a non-interactive way. It means that all the editing is made by predefined instructions, not by arbitrarily typing directly into a text
displayed on the screen. In modern terms, sed can be understood as a template parser: given a text as input, it places custom content at predefined positions or when it finds a match for a
regular expression.
Sed, as the name implies, is well suited for text streamed through pipelines. Its basic syntax is sed
-f SCRIPT when editing instructions are stored in the file SCRIPT or sed -e COMMANDS to execute COMMANDS directly from the command line. If neither -f or -e are present, sed uses the first non-option parameter as the script file.
```
factor `seq 12` | sed 1d

# 1d stand for: delete first line
# 11d would stand for: delete 11th line

factor `seq 12 | sed 1,5d
# We can specify a range of line to delete
```
More than one instruction can be used in the same execution, separated by semicolons. In this case, however, it is important to enclose them with parenthesis so the semicolon is not interpreted
by the shell:
```
factor `seq 12` | sed "1,7d;11d"
```

```
factor `seq 12` | sed "1d;/:.*2.*/d"
```
The regular expression 
```
:.*2.*
```
matches with any occurrence of the number 2 anywhere after a colon, causing the deletion of lines corresponding to numbers with 2 as a factor. **With sed, anything placed between slashes (/) is considered a regular expression and by default all basic RE is supported.**
Instead of deleting a line, sed can replace it with a given text:
```
factor 'seq 12' | sed "1d;/:.*2.*/c REMOVED"
# The instruction c REMOVED simply replaces a line with the text REMOVED. 
```
By far the most used sed instruction is s/FIND/REPLACE/, which is used to replace a match to the
regular expression FIND with text indicated by REPLACE. **For example, the instruction s/hda/sda/ replaces a substring matching the literal RE hda with sda.** Only the first match found
in the line will be replaced, unless the **flag g** is placed after the instruction, as in s/hda/sda/g.

### Combining grep and sed

Commands grep and sed can be used together when more complex text mining procedures are
required. As a system administrator, you may want to inspect all the login attempts to a server, for
example. **The file /var/log/wtmp records all logins and logouts, whilst the file /var/log/btmp
records the failed login attempts.** They are written in a binary format, which can be read by the
commands last and lastb, respectively.
The output of lastb shows not only the username used in the bad login attempt, but its IP address
as well:
```
lastb -d -a -n 10 --time-format notime
```

Option -d translates the IP number to the corrisponding hostname. Option -a puts the hostname in the last column