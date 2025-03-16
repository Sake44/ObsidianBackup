This type of redirection is used to input data to a command, from a specified file instead of a
keyboard. In this case the < operator is used as shown in the example:

```
$ cat < text
Hello!
Hello to you too!
```

This command can be used to translate file contents by modifying the characters in a file in specific ways, like deleting any particular character from a file:

```
$ tr -d "l" < text
Heo!
Heo to you too!
```

Here you can find other [Combinations](Combinations.md).