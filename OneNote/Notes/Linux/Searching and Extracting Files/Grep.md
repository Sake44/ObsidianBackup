## Useful command


#grep is the abbreviation of the phrase “global regular expression print” and its main functionality is to search within files for the specified pattern.

#-i
the search is case insensitive
#-r
the search is recursive (it searches into all files within the given directory and its
subdirectories)
#-c
the search counts the number of matches
#-v
invert the match, to print lines that do not match the search term
#-E
turns on extended regular expressions (needed by some of the more advanced meta-characters like | , + and ?)


### Regular Expressions

It is used to describe bits of text within files, also called regular expressions. Regular expressions are extremely useful in extracting data from text files by
constructing patterns. They are commonly used within scripts or when programming with high level languages, such as Perl or Python.


#### Example list for grep

The following list explains the regular expressions meta-characters that are used to form the
patterns.

```
.
```
Match any single character (except newline)

```
[abcABC]
```
Match any one character within the brackets

```
[^abcABC]
```
Match any one character except the ones in the brackets

```
[a-z]
```
Match any character in the range

```
[^a-z]
```
Match any character except the ones in the range

```
sun|moon
```
Find either of the listed strings

```
^
```
Start of a line

```
$
```
End of a line

```
$ grep "^a" text.txt
aaabbb1
abab2
alien2
$ grep "2$" text.txt
abab2
noone2
alien2
```

Regular expressions also have meta-characters that enable multiplication: 

```
*
```
Zero or more of the preceding pattern

```
+
```
One or more of the preceding pattern

```
?
```
Zero or one of the preceding pattern

Since the **+** character is an *extended* regular expression we need to pass the -E option in **grep** command. 

```
$ grep -E "ab.+" text.txt
aaabbb1
abab2
```