You can set git to automatically apply necessary ssh keys  
depending on your working directory. That way you don't need  
to think about correct credentials and stuff. Here's how:  

in .gitignore do:  
```gitconfig
[includeIF "gitdir:~/personal/"]
	path = "~/.gitconfig-personal"
```

then in .gitignore-personal do:  
```gitconfig
[user]
    name = foo bar
    email = foo@bar.com
[core]
	sshCommand = ssh -i ~/.ssh/<key> -o IdentitiesOnly=yes
```

then in .ssh/config do:  
```sshconfig
Host github-personal
	HostName github.com
	PreferredAuthentications publickey
  	IdentityFile ~/.ssh/<key>
```

You can check if this worked with  
`ssh -T git@github-personal`  

And now, if you did a host alias like here, when you   
add or set a git remote url, you need to use this alias.   
