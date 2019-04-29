# Reflections

## How to create remotes and handling changes in git

It is best sometimes just to understand the syntax before getting verbose and
explaining each concept. Syntax can act as nomenclature to explain succinctly
what every concept deals with. 
<br>The most commonly used commands related to git remote are
```
git remote add origin <github url>    #adding a remote to a git repo
git remote remove origin  #remove a previously created remote
git push origin master  #push to 'origin' the commits in master
```

Before creating the remote to a git version controled repo, we need to first
create a blank repository in github. 
<br>An important point to keep in mind is that while creating the new blank 
repository, all options such as initialize the repository with readme or 
adding a license file must be unchecked. Though this may work later, it is 
easier to push a new local repo, if the remote repository is completely blank.
Also, if the repository on github is blank, GitHub also gives helpful commands
to help in pushing a local repository to the remote.

```
git log --oneline --graph --decorate --all  #useful command to view all recent commits
                                            #in a line along with commits included in 
                                            #the remote branch
```

### PS
one point of note is to always copy the https link and not the ssh link while
creating the remote branch for a local repo. There are some technical reasons
for this, but for now it is best to remember that the ssh link would require
more work arounds than the http link.

### To import commits in the remote repo

```
git pull origin master
```
The pull statement does three steps:
- Fetches commits into the origin remote
- Sets the local tracking branch 'origin/master' to the updated remote repo commits
- Merges the 'origin/master' into the master branch.

## Git fetch
If there are unsynced commits in the remote branch of the repo, and there are further
unsynced commits to the local repo over the last synced tracking branch, a git pull would
not work correctly.
You now need to do a fetch and merge and then push to get the remote and the local completely
and perfectly in sync.

```
git fetch origin master  # Fetches the remote's master branch and merges into the
                         # the remote tracking branch. [origin/master in most cases]

git merge origin/master  # Merges the origin/master branch into the local master
                         # Also gets the remote tracking branch and the local master branch
                         # in sync.

git push origin master   # Pushes the final commit history to the remote.
                         # This brings everything back in sync [ the remote repo, the remote tracking
                         # branch and the local master]
```