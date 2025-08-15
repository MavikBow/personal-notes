scripts that solve my personal will to have mkdir + cd  

#Scripts:
=============================

I found four ways to make this work, it only makes the process just   
a bit less finicky, and I haven't tested the edge cases, but here it is.  

```bash
#!/bin/bash

mkcdir() 
{
	mkdir -p "$1" && cd "$1"
}
```
https://github.com/rohan221102/mkcdir/blob/main/mkcdir.sh  

Here's something even better:  
```bash
# make a directory and cd to it
mcd()
{
    test -d "$1" || mkdir "$1" && cd "$1"
}
```
https://unix.stackexchange.com/questions/6628/what-customizations-have-you-done-on-your-shell-profile-to-increase-productivity  

also you can call  
```bash
mkdir <blah>
cd "$_"
```
https://unix.stackexchange.com/questions/125385/combined-mkdir-and-cd  

You might get away with just `cd $_` but the name must lack spaces.  
  
Even better:  
```bash
mkdir <blah>
cd !$
```
https://unix.stackexchange.com/questions/9123/is-there-a-one-liner-that-allows-me-to-create-a-directory-and-move-into-it-at-th  

This one is easier to type, and is "space resistant" as far as I can tell. Thank you, Rob.  
Funnily enough, from Rob's words it seems he never thought of implimenting   
this complimentary action into mkdir itself.  
