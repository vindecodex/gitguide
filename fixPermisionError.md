***
## Fixing Permision Error

1. Generate ssh key
>`$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

*if you have already an id_rsa on your ~/.ssh directory please change the directory of your new created key when prompted after running above command*
>example /Users/you/.ssh/anything/yourkeyname

2. Add our key to ssh-agent

> `$ eval "$(ssh-agent -s)"`
> `$ ssh-add ~/.ssh/anything/yourkeyname`
> Enter your password, use the password during the creation of key

3. `vi ~/.ssh/config` or `nano ~/.ssh/config` or any text editor you have

*Add this line or if it exist change it same below:*
```php
Host github.com
  HostName github.com
  IdentityFile ~/.ssh/anything/yourkeyname
```

4. Go to your github **settings > SSH and GPG keys > New SSH Key**
>Add title to the machine where your ssh is created example CompanyLaptop or MyMacPro etc...

5. For the Key we are going to copy the content of our generated key.

**For Mac/Bash:**
``` php
//this will copy the content of yourkeyname to our clipboard so that we can paste it on the github
$pbcopy < ~/.ssh/anything/yourkeyname
```

6. Then Click Add ssh key

*if you want to change something it can be found at:*
```php
$vi ~/.gitconfig
```
# Or google it :)