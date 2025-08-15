I want there to be a single command that combines  
the actions of creating a directory and cd'ing into it.  

Here are some arguements I found pro and anti this feature:  

#Pro:
=============================

> Me:
```
This is a very common workflow. You create a directory
(often with a very long name), and then you have to retype
that name, or do other finicky moves to get there.
```

-----------------------------

> Me:
```
git has the feature to create a new branch and immediately go to it.
In fact, there are several ways to do that in one command.
those are

`git checkout -b <branch>`
`git switch -c <branch>'

the latter was addes later, so they didn't think it redundant even after
already having a command to do this exact same action.
```

> Internet:
```
oh-my-zsh apparantly has `mkcd ` and `take` commands that do exactly that
```
https://github.com/ohmyzsh/ohmyzsh/wiki/Cheatsheet

#Anti:
=============================

> Bob Proulx:

```
I don't think this is a good idea.  It could be added.  But does it
really gain you anything over calling mkdir -p?  I don't think so.  It
would simply add code bloat to the program.

Plus it wouldn't be portable.  Other implementations wouldn't have it.
It is only of marginal benefit if at all and so other implementations
might never have it.  In any case you would need to wait years before
the feature trickled down to where you could use it reliably.  Also
you can always accomplish this yourself with a shell script.  In
general things that can be easily encapsulated in a shell script are
not good additions to the utilities.

Adding that option is counter to The Unix Philosophy.  Small is
beautiful.  Make each program do one thing well.  Choose portability
over efficiency.  Use shell scripts to increase leverage and
portability.
```

[taken from his arguing against making a 'mv -p' feature]  
https://debbugs.gnu.org/cgi/bugreport.cgi?bug=5926  
Message #8  

-----------------------------
My comment:  
This does seem like a valid arguement, because git is it's own thing  
and having branch creation and switching be done in one command simply  
calls git's internal methods. Whereas giving mkdir capabilities of cd might  
go against the aforementioned Unix Philosophy.  

#Pro:
=============================

> f0rhum:
```
Would mv be discarded to the benefit of cp + rm?
Ok, I know we can't because mv also does in place rename. 
But when it's time to real move who does use cp then rm?

```

https://debbugs.gnu.org/cgi/bugreport.cgi?bug=5926  
Message #50  

-----------------------------
My comment:  
Bob then explains that basically mv provides this:  
if the action is within the same file system, then an atomic rename(2)  
is called.  If moving across different file systems, then cp + rm is called.  
I guess it takes off the cognitive load off of the user?  


> f0rhum:
```
The same "You have to know if the parent exists" argument that was opposed
to this request could have also been opposed: "You have to know if you are
moving in the same file system or an other,
so we stick to rename+cp+rm, no need for mv at all, small is beautiful,
do one thing and do it well".
```

https://debbugs.gnu.org/cgi/bugreport.cgi?bug=5926  
Message #56  

-----------------------------
My comment:  
This unfortunatelly wasn't answered anywhere. My guess is that, at the end  
of the day, `move` is only there as a legacy heritage from Unix.   
We can't get rid of it now not to break legacy scripts. (or can we?)  
I'm starting to question what `portability` means in the Unix phisolophy.  
  
Because if it means code runs anywhere then we keep it as legacy, and as such,  
mark mv as a legacy utility.  
  
And if it means code gets smaller to fit in more places, then me must do away  
with mv. It can be replaced with a shell script to fall in accordance with   
the unix philosophy. Like Bob said "Use shell scripts to increase leverage   
and portability."  
  
And in Unix we have `mv` just because "move" is a single English word that  
represents a "single" logical action to a person. And that's a crap argument.  
