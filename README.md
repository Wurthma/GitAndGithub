# Git helper

After install git, we need to configure name and e-mail with below commands:

`git config --global user.name "Seu nome aqui"`
`git config --global user.email "seu@email.aqui"`

We can change the parameter to `--local` to configure only for the currently repository.

## Most basic commands

Init Git version control in a project directory: `git init`
Check status: `git status`
Track files: `git add .` or for unique file `git add <myFileName>`
Untrack files `git rm --caached .` or for unique file `git rm --caached <myFileName>`
Commit tracked files: `git commit -m "My commit message"`
Check the list of commits: 
	- Custom: `git log` or `git log --graph` to more detailed
	- Basic: `git log --oneline`
	- Detailed: `git log -p`
	
## .gitignore

We can use the **.gitignore** file to ignore all files and folders that should not be tracked by git.

We can manually create .gitignore file or user the command `git add .gitignore`.

## Using, update and send data to remote repositories

`git remote -v` to list all remote repositories.

`git remote add <someRemoteName> <NameOrUrlRemoteRepository>` to add a remote repository

`git remote rename <someRemoteName>` to rename the configured remote repository.

`git remote set-url <someRemoteName> <NameOrUrlRemoteRepository>` to alter the remote repository URL.

`git clone <NameOrUrlRemoteRepository>` to clone some repo.

below will push your code to the main branch of the remote repository defined with <someRemoteName> and `-u` let you point your current local branch to the remote maain branch:

`git push -u <someRemoteName> main`

`git pull` will get all updated data from remote repo.

## Branchs

`git branch` to list branchs.

`git branch feature-payment` to create a new branch named **feature-payment**.

`git checkout feature-payment` change to branch **feature-payment**.

We can also use `git checkout -b <branchName>` this will create a new branch and change to it.

`git branch -d <branchName>` to delete a branch.

`git branch -D <branchName>` to force delete a branch.

### Merging branchs

`git merge <branchName>` to merge currently branch from specified branch. This will create a new commit.

When a merge is created, a screen will be available to edit the text of the commit message in the **VIM** editor, to save the message we can use **:x**.

`git rebase <branchName>` rebase will commit everything from the specified branch without merge.

The problem with **rebase** is that it changes history, as do other git commands (such as those that take the --hard attribute). For this reason, it is only recommended in very specific cases. Git is not premised on protecting the change history at all costs but, by default, preserving it.

If we try to merge or rebase some branches that have conflicts with our current branch the commit will inform us that there are conflicts. This will generate lines with special characters **<<<<<**, **======** and **>>>>>>** to identify conflicting lines in files with conflict.

After resolving the conflicts we should run `git commit` and git will know that we are done resolving the conflicts.

Using `git diff` we can see the modifications not commited yet.

...or `git diff ea43a88..9a1420c`  to see the difference between the two commmits specified.

## Undoing

Use `git checkout -- <fileName>` to undo all changes not committed

...or, if changes have already been added to tracked files with `git add` use: `git reset HEAD <fileName>`

This will remove the commit, but the changes will remain in the file and to remove the `git checkout -- <fileName>` command must be used.

...or, if changes have already been added committed use: `git revert <git_hash_id>`

## Stash

With `git stash` we can safaly store changes to use/recover later.

Use `git stash list` to list all availables stashes.

To recover a stash use `git stash apply 0` where **0** is the number of the stash that will be recovered.

Use `git stash drop` to remove stash

We can also use `git stash pop` to recover and delete the stash.

## Time traveling

Using `git log --oneline` we can see git commits hash ids and using then we can see the code at this moment:

`git checkout ea43a88`

By doing this we will be in code that is not monitored by git, if we want to change it we need to create a branch from it with:

`git checkout -b <branchName>`

## Tags and releases

`git tag -a v1.0.0` to create a tag with name **v1.0.0**

...or `git tag -a v1.0.0 -m "My tag message"` to create a tag with some message.

`git tag` list all thags of the currently repo.

After create a tag, we need to push it.
