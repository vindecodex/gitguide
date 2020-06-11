# Guide for Multiple Git Users with SSH.

Solution for the problem about switching work account and personal account.

1. First we need to generate our ssh key. ** This can be skipped if you have already **


below is personal ssh key


`ssh-keygen -t rsa -b 4096 -C "your_personal_email@example.com"


```
Note that this keys must be separate files so make sure you change the default file name during creation you will be promted about this

example for your personal: ~/.ssh/personal_rsa
example for your work: ~/.ssh/work_rsa
```

below is for your work ssh key


`ssh-keygen -t rsa -b 4096 -C "your_work_email@example.com"`


[For more detailed information check this out](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

start the ssh agent in the background

`eval "$(ssh-agent -s)"`

Add the keys to the ssh agent

```
ssh-add ~/.ssh/personal_rsa
ssh-add ~/.ssh/work_rsa
```

Copy the .pub files of your keys and add it to your github ssh settings

2. We now need to modify our ssh config. ** If you dont have a config you can create manually with touch **

If there is no config exist create manually

`touch ~/.ssh/config`

Edit the config with any editor

`vi ~/.ssh/config`

Add the following lines

```
\# Personal Account
Host github.com-personal
		HostName github.com
		User git
		IdentityFile ~/.ssh/personal_rsa

\# Work Account
Host github.com-work
		HostName github.com
		User git
		IdentityFile ~/.ssh/work_rsa
```

** Pattern for switching **

`git remote set-url origin [User]@[Host]:[repo-user]/[reponame].git`

`git config --global user.name="name of your personal git" user.email="email of your personal git"

##### To replace this pattern with Personal Account

`git remote set-url origin git@github.com-personal:vindecodex/gitguide.git`

`git config --global user.name="personal" user.email="personal@email.com"`

##### To replace this pattern with Work Account

`git remote set-url origin git@github.com-work:vindecodex/gitguide.git`

`git config --global user.name="work name" user.email="work@email.com"`

##### Checking Current origin url

`git config remote.origin.url`

##### We can also check or test or ssh config if working

`ssh -T [User]@[Host]` => `ssh -T git@github-personal` or `ssh -T git@github.com-work`

##### This will console your associated account on each Host.

On setting up the `git config --global` better to create alias for it to make it shorter.

```
alias gitpersonal="git config --global user.name="personal" user.email="personal@email.com"

alias gitwork="git config --global user.name="work" user.email="work@gmail.com"
```

Now everytime we clone a repo `ssh` must be selected instead of `HTTPS`

