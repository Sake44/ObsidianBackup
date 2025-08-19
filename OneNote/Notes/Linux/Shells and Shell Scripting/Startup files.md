It's time we saw what startup files get executed by what shell. 
Note that system wide or global scripts are placed in the /etc/ directory, whereas local or user-level ones are found in the user’s home (~).

### Interactive Login Shell

#### Global level
```
/etc/profile
```
This is the system-wide .profile file for the Bourne shell and Bourne compatible shells (bash
included). Through a series of if statements this file sets a number of variables such as PATH
and PS1 accordingly as well as sourcing — if they exist — both the file /etc/bash.bashrc and
those in the directory /etc/profile.d.
```
/etc/profile.d
```
This directory may contain scripts that get executed by /etc/profile.

#### Local level
```
~/.bash_profile
```
This bash specific is used for configuring the user environment. It can also be used to source both ~/.bash_login and ~/.profile.
```
~/.bash_login
```
Also Bash specific, this file will only be executed if there is no ~/.bash_profile file. Its name
suggests that it should be used to run commands needed on login.
```
~/.profile
```
This file is not bash specific and gets sourced only if neither ~/.bash_profile nor ~/.bash_login exist.
Thus, the main purpose of ~/.profile is that of checking if a Bash shell is being run and — if so — sourcing ~/.bashrc if it exists. It usually sets the variable PATH so that it includes the user’s private ~/bin directory if it exists.

### Interactive Non-Login Shell 

#### Global level
```
/etc/bash.bashrc
```
This is the system-wide .bashrc file for interactive bash shells.

#### Local level
```
~/.bashrc
```
In addition to carrying out similar tasks to those described for /etc/bash.bashrc at a user level (such as checking the window size or if being run interactively), this Bash specific file usually sets some history variables and sources ~/.bash_aliases if it exists. Apart from that, this file is normally used to store users' specific aliases and functions.


### The origin of startup files
SKEL is a variable whose value is the absolute path to the skel directory. **This directory serves as a template for the file system structure of users' home directories.** It includes the files that will be inherited by any new user accounts created.