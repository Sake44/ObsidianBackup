How do we identify values for each of our environment variables? With #env 
```
env
```

The #echo command will print to the screen whatever you tell it to.
```
echo "Whatever you want to print"
```

But there is something else you can do with #echo. When you feed it the name of an environment variable — and tell it that this is a variable by prefixing the variable name with a $ — then, instead of just printing the variable’s name, the shell will expand it giving you the value.
```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/sn
ap/bin
```

### Creating New Environment Variables

You can add your own custom variables to your environment. The simplest way is to use the =
character. The string to the left will be the name of your new variable, and the string to the right
will be its value: 
```
myvar=hello
echo $myvar
```
A variable you create the way we just did is only going to be available locally — within the
immediate shell session. If you start up a new #shell — or close down the session using #exit — the variable will not go along with you.
You can type **export myvar** to pass the variable to any child shells that you may subsequently open.
#### Deleting Environment Variables

To delete an ephemeral variable we can use #unset command: 
```
unset myvar (without $)
```
Running #set by itself will display lots of output, but it is really not all that different from what env gave you.
With #set and #env we can list all variable. The main difference between those commands is that #env list only exported variables (the one related to process). 

