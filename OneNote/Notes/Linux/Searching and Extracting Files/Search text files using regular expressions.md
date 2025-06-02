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