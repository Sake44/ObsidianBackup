In most Linux distributions, #vi — abbreviation for “visual” — is pre-installed and it is the standard editor in the shell environment. Vi is an interactive text editor, it shows the file content on the screen as it is being edited. As such, it allows the user to move through and to make modifications anywhere in the document.
There are different execution modes for vi where program behavior changes. The most common are: **insert mode and normal mode.**

## Normal Mode
Normal mode — also known as command mode — is how vi starts by default. In this mode,
keyboard keys are associated with commands for navigation and text manipulation tasks. Most
commands in this mode are unique keys. Some of the keys and their functions on normal mode
are:

```
0, $
```
Go to the beginning and end of the line.
```
1G, G
```
Go to the beginning and end of the document.
```
(, )
```
Go to the beginning and end of the sentence.
```
{, }
```
Go to the beginning and end of the paragraph.
```
w, W
```
Jump word and jump word including punctuation.
```
h, j, k, l
```
Left, down, up, right.
```
e or E
```
Go to the end of current word.
```
/, ?
```
Search forward and backwards.
```
i, I
```
Enter the insert mode before the current cursor position and at the beginning of the current
line.
```
a, A
```
Enter the insert mode after the current cursor position and at the end of the current line.
```
o, O
```
Add a new line and enter the insert mode in the next line or in the previous line.
```
s, S
```
Erase the character under the cursor or the entire line and enter the insert mode.
```
c
```
Change the character(s) under the cursor.
```
r
```
Replace the character under the cursor.
```
x
```
Delete the selected characters or the character under the cursor.
```
v, V
```
Start a new selection with the current character or the entire line.
```
y, yy
```
Copy (yanks) the character(s) or the entire line.
```
p, P
```
Paste copied content, after or before the current position.
```
u
```
Undo the last action.
```
Ctrl-R
```
Redo the last action.
```
ZZ
```
Close and save.
```
ZQ
```
Close and do not save.
Most editing tasks are combinations of multiple commands. For example, the key sequence vey is
used to copy a selection starting at the current position until the end of the current word. Command repetition can also be used in combinations, so v3ey would copy a selection starting at
the current position until the end of the third word from there.

### Colon Commands

The normal mode also supports another set of vi commands: the colon commands. Colon
commands, as the name implies, are executed after pressing the colon key : in normal mode.
Some of the most common colon commands are indicated here: 

```
:s/REGEX/TEXT/g
```
Replaces all the occurrences of regular expression REGEX with TEXT in the current line. It
accepts the same syntax of command sed, including addresses.
```
:!
```
Run a following shell command.
```
:quit or :q
```
Exit the program.
```
:quit! or :q!
```
Exit the program without saving.
```
:wq
```
Save and exit.
```
:exit or :x or :e
```
Save and exit, if needed.
```
:visual
```
Go back to navigation mode.