Git 
Resetting a branch
First, get the SHA before the commit you want to reset too:
git log --oneline
Then use the following commands:
git reset SHA --soft
git commit -m 'new commit message'
git push origin BRANCH --force
Renaming a branch locally and push to Github
- Rename your local branch:

- If you are on the branch you want to rename:
git branch -m new-name

- If you are on a different branch:
git branch -m old-name new-name

- Delete the old-name remote branch and push the new-name local branch:
git push origin :old-name new-name

- Reset the upstream branch for the new-name local branch:
Switch to the branch and then:
git push origin -u new-name
Work on an old commit:
Get the old SHA:
get log --online
      You’ll see something like:
d9ed0c007 (HEAD -> rout-4077-resizable-drawers, origin/rout-4077-resizable-drawers) create custom hooks
45139493c code smell
c58d3e373 inverse if/else for transisiton + remove pointer handler
f346fb18d simplify styled drawer even more + break it up
8d693f6a4 try and address complexity in StyledDrawer
b4964bce7 update styled drawer isResizing
In this case, we want b4964bce7
If you want to fool around and then come back to where you were:
// This will detach your HEAD, that is, leave you with no branch checked out:
git checkout b4964bce7
Or if you want to make commits while you're there, go ahead and make a new branch while you're at it:
git checkout -b new-branch b4964bce7
Get current branch:
git branch --show-current
Delete all git branches (apart from develop and master):
git branch | grep -v "develop" | grep -v "master" | xargs git branch -D
