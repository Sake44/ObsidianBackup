---
---
to set automatically an upstream branch to a new branch
```
git config --global push.autoSetupRemote true
```

**Getting & Creating Projects**
**Branching & Merging**

Initialize a local Git repository
```
git init
```

|     |     |
| --- | --- |
| git clone<br>ssh:// git@github.com/ \[username\]/\[repositoryname\].git | Create a local copy of<br>a remote repository |
| git status | Check status |
| git add \[file-name.txt\] | Add a file to the staging<br>area |
| git add -A | Add all new and changed<br>files to the staging area |
| git commit -m "\[commit message\]" | Commit changes |
| git rm -r \[file-name.txt\] | Remove a file (or folder) |

## Create repository from command line

![[Screenshot from 2024-06-18 15-17-07.png]]

1\. Utilizzare i Token di Accesso Personale (PAT)
GitHub non supporta più l'autenticazione con la password tramite HTTPS. Invece, utilizza un Token di Accesso Personale (PAT) come password. Ecco come fare:

Crea un Token di Accesso Personale:

Vai alla pagina Personal Access Tokens su GitHub.
Clicca su "Generate new token".
Dai un nome al tuo token e seleziona le autorizzazioni necessarie (almeno repo per accedere ai repository privati).
Clicca su "Generate token" e copia il token generato (conserva questo token in un luogo sicuro).

```
git branch
```
List branches (the asterisk denotes the current branch)
```
git branch -a
```
List all branches (local and
remote)
```
git branch \[branch name\] Create a new branch
```
```
git branch -d \[branch name\] Delete a branch
```
```
git push origin --delete \[branch name\] Delete a remote branch
```
```
git checkout -b \[branch name\]
```
Create a new branch and switch to it
```
git checkout -b \[branch name\] origin/\[branch name\]
```
Clone a remote branch and switch to it
```
git branch -m \[old branch name\] \[new branch name\]
```
Rename a local branch
```
git checkout \[branch name\] 
```
Switch to a branch
```
git checkout -
```
Switch to the branch last checked out
```
git checkout -- \[file-name.txt\] 
```
Discard changes to a file
```
git merge \[branch name\]
```
Merge a branch into the active branch

Merge a branch into a target branch
```
git merge [source branch] [target branch]
```
Stash changes in a dirty working directory
```
git stash
```
Inspection & Comparison

### Sharing & Updating Branches

Push a branch to your remote repository
```
git push origin [branch name]
```

Push changes to remote repository (and remember the branch)
```
git push -u origin [branch name]
```
Push changes to remote repository (remembered branch)
```
git push
```

Delete a remote branch
```
git push origin --delete [branch name]
```
Update local repository to the newest commit
```
git pull
```

Pull changes from remote repository
```
git pull origin [branch name]
```
Add a remote repository
```
git remote add origin
ssh:// git@github.com/ [username]/[repositor y-name].git
```
Set a repository's originbranch to SSH
```
git remote set-url origin
ssh:// git@github.com/ [username]/[repository-name].git
```

**Pulling into a dirty tree**
When you are in the middle of something, you learn that there are upstream changes
that are possibly relevant to what you are doing. When your local changes do not
conflict with the changes in the upstream, a simple git pull will let you move
forward.
However, there are cases in which your local changes do conflict with the upstream
changes, and git pull refuses to overwrite your changes. In such a case, you can
stash your changes away, perform a pull, and then unstash, like this:

```
$ git stash
$ git pull
$ git stash pop
```

**Empty Commit**
```
git commit --allow-empty -m "Empty-Commit"
```
Specifico per progetti che usano nvm. CHECKSTYLE
Controllare version:
```
nvm: nvm -v
```
nvm use permette di impostare la versione node del progetto.
Controllare nel package.json se è presente ESLINT.
runnare npm run ${eslint}
Command
Description
```
git log View changes
git log --summary View changes (detailed)
git log --oneline View changes (briefly)
git diff [source branch] [target branch]
```
Preview changes before merging

## SSH Connect

```
ssh-keygen -t ed25519 -C "your_email@example.com" -f C:\Users\andre\.ssh\gitKey
```
