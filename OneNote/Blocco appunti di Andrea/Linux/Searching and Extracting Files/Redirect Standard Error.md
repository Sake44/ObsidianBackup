
In order to redirect just the error messages, a user will need to employ the 2> operator followed
by the name of the file in which the errors will be written.

```
$ find /usr games 2> text-error
/usr
/usr/share
/usr/share/misc
---------Omitted output----------
/usr/lib/libmagic.so.1.0.0
/usr/lib/libdns.so.81
/usr/games
$ cat text-error
find: `games': No such file or directory
```

As well as the standard output, the standard error can also be appended to a file with the 2>>
operator.

```
$ sort /etc 2>> text-error
$ cat text-error
sort: read failed: /etc: Is a directory
```

There is one particular file that technically is a #bitbucket (a file that accepts input and doesn’t do
anything with it): **/dev/null**. You can redirect any irrelevant information that you might not
want displayed or redirected into an important file, as shown in the example below:

```
$ sort /etc 2> /dev/null
```

Let's see how to [Redirect Standard Input](Redirect%20Standard%20Input.md).


