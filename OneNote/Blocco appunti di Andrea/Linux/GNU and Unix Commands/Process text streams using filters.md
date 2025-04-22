
One major way of making programs work together is through #piping and #redirections. Pretty much all of your text manipulation programs will get text from a standard #input (stdin), output it to a standard #output (stdout) and send eventual errors to a standard #error output (stderr).

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



