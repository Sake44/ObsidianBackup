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

