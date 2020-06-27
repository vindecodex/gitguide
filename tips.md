### Cleaner git log command

`git log --all --graph --decorate --online`

### Staging file with specific line of code

`git add -p <file>`

press `s` to split by block

choose which block of code will be staged and press `y` for yes and `n` for no.

### Creating local remote

1. Firt initialize a local remote by creating a directory initialize git with bare.

`cd folder/where/yourremote

`git init --bare`

2. Now create your project and initialize git.

`cd folder/where/yourrepo`

`git init`

3. Now add a remote with anyname for this example we name remote to origin.

`git remote add <name> <url or locationPath>`

example:

`git remote add origin /home/yourremote`

4. Now pushing changes from our repository to the remote.

`git push <remote_name> <localBranch>:<remote_branch>`

example:

`git push origin master:master`

From our local master branch we push it to remote master branch.
