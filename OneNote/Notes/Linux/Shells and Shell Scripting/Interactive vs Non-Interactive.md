### Interactive / Non-Interactive Shells
This kind of shell refers to the interaction that takes place between the user and the shell: The
user provides input by typing commands into the terminal using the keyboard; the shell provides output by printing messages on the screen.

### Login / Non-Login Shells
This kind of shell refers to the event of a user accessing a computer system providing its
credentials, such as username and password.

### Interactive login shells
Interactive login shells are executed when users log into the system and are used to customize
users' configurations according to their needs.

### Interactive non-login shells
Interactive login shells are executed when users log into the system and are used to customize
users' configurations according to their needs

On the other hand, non-interactive shells do not require any kind of human interaction. Thus,
these shells do not ask the user for input and their output — if any — is in most cases written to a
log.

Non-interactive login shells are quite rare and impractical. Their uses are virtually non-existent
and we will only comment on them for the sake of insight into shell behaviour. Some odd
examples include forcing a script to be run from a login shell with 
```
/bin/bash --login <some_script>
```



