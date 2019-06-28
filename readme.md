***
## ~/.gitconfig

> Configure username

``` php
$ git config --global user.name "[name]"
```

> Configure email

``` php
$ git config --global user.email "[email address]"
```

***
## Create New Repository
1. Create Repo on Github
2. `git init` on local directory
3. copy repo url (use the ssh)
4. `git remote add origin [repo url you copy on step 3]`
5. `git add .`
6. `git commit -m "your message"`
7. `git push origin master` (if got Permission Error try [this](https://github.com/vindecodex/gitguide/blob/master/fixPermisionError.md))
## Or Download Existing Repo
``` php
git clone [urlofrepo]
```
***
## Create branch and merging branch to the master
>You can create branch to create/upgrade/edit the existing file without affecting the main/master branch

```php
$ git branch branchname
```

>To enter to our new branch

```php
$ git checkout branchname
```

>You can checkout different branch created by anyone on your project

```php
$ git add .
$ git commit -m "Your message here"
$ git push origin branchname
```

>Adding new files in our branch

>After pushing to origin branchname a link will be given to the terminal, click it while pressing cmd on mac, i think ctrl for windows

>It will redirect to the pull request on github page

>Click Create pull request

```php
$ git checkout master
``` 

>To go back to the master branch

```php
$ git merge branchname
$ git push origin master
```

>To merge our changes on our branch to the master

>And push to our master to fully added to the main project

***

## Check for changes

```php
$ git status
```

>check if there is added, deleted or modified files so that you can start running the `git add` and `git commit`

```php
$ git diff
```

>to see changes of files that are not yet added by `git add .` to the master branch

```php
$ git diff branchA branchB
```

>to see changes between two branches

```php
$ git diff --staged
```

>to see changes of files that are already added by `git add .` to the master

>after you `git add .` those files are in staging or ready to be commited

```php
$ git reset filename
```

>to unstage the files but the contents of your current work will not be affected, it will just remove the added files for staging

```php
$ git log
```

>display all commited versions

## Rebase

>if you commited two times with just a few changes and doesnt deserve to be commited then we can delete it without affecting the contents, only the commit will be removed but not its content

```php
$ git rebase -i HEAD~2 //we use 2 here because we want the two commit will be modified
```

***
>If you see some improvements please help by creating a pull request.


***