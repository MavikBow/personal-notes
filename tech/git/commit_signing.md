You can set git to automatically sign your commits to prevent identity theft.  
Since git 2.34 you can use same SSH key you use to push commits.  
  
```gitconfig
[user]
    ...
    signingkey = ~/.ssh/<private-key>
[gpg]
    format = ssh
[commit]
    gpgsign = true
```
  
Yes, apparently you're meant to use you *private* key here.  
But public is also acceptable.  
  
```plain text
If gpg.format is set to ssh this can contain the path to either   
your private ssh key or the public key when ssh-agent is used.   
```
  
See `man git config` user.signingKey paragraph  
