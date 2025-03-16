**ls** has up until now only shown us the files and sub directories of a location, but
cannot tell us the contents of these sub directories.

Let's compare **tree** output with **recursive list** output.

```
$ tree /home/user
user
└── Documents
├── Mission-Statement
└── Reports
└── report2018.txt

$ ls -R ~

/home/user/:
Documents

/home/user/Documents:
Mission-Statement
Reports

/home/user/Documents/Reports:
report2018.txt
```

Recursion is particularly important in file modification commands such as copying or removing
directories. For example, if you wanted to copy the Documents sub directory, you would need to
specify a recursive copy in order to extend this command to all sub directories.