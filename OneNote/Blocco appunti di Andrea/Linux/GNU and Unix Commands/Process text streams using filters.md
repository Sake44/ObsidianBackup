
One major way of making programs work together is through 
#piping and #redirections. Pretty much all of your text manipulation programs will get text from a standard #input (stdin), output it to a standard #output (stdout) and send eventual errors to a standard #error output (stderr).

The > (greater than) tells cat to direct its output to the mytextfile file, not the standard output.
```
cat > mytextfile
Whatever i write will be redirect to my text file.

cat mytextfile
Whatever i write will be redirect to my text file.
```

If we want to redirect our text file to a new one (copy), we can:
```
cat mytextfile > mytextfile
```
With echo we and redirection operator (>>) we can also append to a file a new text.

```
echo 'This is a new line' >> mynewtextfile
```
So far we have used redirections to create and manipulate files. We can also use pipes (represented by the symbol |) to redirect the output of one program to another program. Another way to filrer a file is to use directly the command #grep:

```
grep cat <filename>.txt
```

#### Reading Compressed Files
There are commands that handle compressed files (#bzcat for #bzip, #xzcat for #xz compressed files and #zcat for #gzip compressed files). 

```
gzip <filename>

zcat <filename>
```

#### Getting a portion of a file
If only the start or end of a file needs to be reviewed, there are other methods available. Thecommand head is used to read the first ten lines of a file by default, and the command tail is used to read the last ten lines of a file by default.

```
# elevate your privileges to sudo
sudo head <filename>

sudo tail <filename>

# we can pipe the command head with command nl (to output number of line)
sudo head <filename> | nl

# we can also pipe the command tail with command wc (to count number of words within doc)
sudo tail <filename> | wc -l
```
Should an administrator need to review more (or less) of the beginning or end of a file, the -n option can be used to limit the commands' output:

```
sudo tail -n 5 <filename>
```

##### Basic of sed, the Stream Editor
Most of what we can do with grep we can also do with sed — the stream editor for filtering and
transforming text. 

We can use sed to list only the lines containing the string cat:
```
sed -n /cat/p < <filename>
```
We have used the less-than sign < to direct the contents of the file ftu.txt into into our sed
command. The word enclosed between slashes (i.e. /cat/) is the term we are searching for. The
-n option instructs sed to produce no output (unless the ones later instructed by the p command).

If we do not use the -n option, sed will print everything from the file except for what the d
instructs sed to delete from its output.
A common use of sed is to find and replace text within a file. Suppose you want to change every occurrence of cat to dog. You can use sed to do this by supplying the s option to swap out each instance of the first term, cat, for the second term, dog:

```
sed s/cat/dog < <filename>
    swap/word to swap/ new value
```


Rather than using a redirection operator (<) to pass the ftu.txt file into our sed command, we
can just have the sed command operate on the file directly. We will try that next, while
simultaneously creating a backup of the original file:

```
sed -i.backup s/cat/dog <filename>
```
The -i option will perform an in-place sed operation on your original file. If you do not use the.backup after the -i parameter, you would just have rewritten your original file. Whatever you use as text after the -i parameter will be the name the original file will be saved to prior to the modifications you asked sed to perform.

#### Ensuring data integrity

What is a checksum? 

A checksum is a value derived from a mathematical computation, based on a cryptographic hash function, against a file. There are different types of cryptographic hash functions that vary in strength.

We can obtain the checksum of a file based on a specific cryptographic hash functions: 

```
sha256sum <filename>
#Example
345452304fc26999a715652543c352e5fc7ee0c1b9deac6f57542ec91daf261c ftu.txt
```

The long string of characters preceding the file name is the SHA256 checksum value of this text file.
We can also create a file that contains the output of our computation based on crypt functions
```
sha256sum <filename> > <filename where is redirect>
```

Now, to verify the ftu.txt file, we just use the same command and supply the filename that
contains our checksum value along with the -c switch:

```
sha256sum -c <filename>
```

The value contained within the file matches the calculated #SHA256 checksum for our ftu.txt
file, just as we would expect. However, if the original gile were modified the value check would fail. In such cases we know that our file is bad or corrupted, and we can not trust the 
integrity of its contents.

To prove it: 

```
echo "new entry" >> <filename> (append to the previous file where checksum was calculated)

# Output example 
$ sha256sum -c sha256sum.txt     
newfile.txt: FAILED
sha256sum: WARNING: 1 computed checksum did NOT match     
```

And we see that the checksum does not match what was expected for the file. Therefore, we coul not trust the integrity of this file.

#### Looking deeper into files
The octal dump (od) command is often used for debugging applications and various files. By itself, the #od command will just list out a file’s contents in octal format. We can use our ftu.txt file from earlier to practice with this command:

The first column of output is the byte offset for each line of output. Since od prints out information in octal format by default, each line begins with the byte offset of eight bits, followed by eight columns, each containing the octal value of the data within that column.

We can also see the output in #hexadecimal format, using the -x option. 

One handy use of the od command is for debugging scripts. For example, the od command can
show us characters that are not normally seen that exist within a file, such as newline entries. We can do this with the -c option, so that instead of displaying the numerical notation for each byte, these column entries will instead be shown as their character equivalents:

```
od -c <filename>
```

All of the newline entries within the file are represented by the hidden \n characters. If you just want to view all of the characters within a file, and do not need to see the byte offset information, the byte offset column can be removed from the output like so:

```
od -An -c <filename>
```



