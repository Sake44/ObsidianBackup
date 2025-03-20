This command is primarily used to change a user’s password. Any user can change their
password, but only root can change any user’s password.
Depending on the passwd option used, you can control specific aspects of password aging:
```
-d
```
Delete the password of a user account (thus setting an empty password, making it a
passwordless account).
```
-e
```
Force the user account to change the password.
```
-l
```
Lock the user account (the encrypted password is prefixed with an exclamation mark).
```
-u
```
Unlock the user account (it removes the exclamation mark).
```
-S
```
Output information about the password status for a specific account.