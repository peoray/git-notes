Maybe add a bookmark on top with all the queries you are giving solution to so someone can move to the one they want.


#### To delete a local branch:
**N.B:You cannot delete the branch you are currently on.** 

If you are in the same branch that you want to delete, run:

`git checkout <another-branch>` to switch to another branch(because you can't delete a branch you are currently on)

Then delete the branch you want:

`git branch -d <branch-name>`

---

#### To delete a remote branch:

`git push --delete <remote_name> <branch_name>`

---
### To remove remote origin from Git repo:
Instead of removing and re-adding, you can do this:

`git remote set-url <origin> git://<new.url.here>`

If you insist on deleting it:

`git remote rm <origin>`

To add another remote:

`git remote add <origin> <yourRemoteUrl>`

---

#### To update a GitHub forked repository:

Add the remote, call it "upstream":

`git remote add <upstream> https://github.com/<whoever>/<whatever.git>`

Fetch all the branches of that remote into remote-tracking branches, such as upstream/master:

`git fetch <upstream>`

Make sure that you're on your master branch(or the main branch):

`git checkout master`

Updating your fork from original repo to keep up with their changes:

`git merge upstream/master`

See [here](https://github.com/KirstieJane/STEMMRoleModels/wiki/Syncing-your-fork-to-the-original-repository-via-the-browser) on how to update your forked repo via the browser.

---

#### To delete a .git file from your repo so you can initialized git again: 
`rm -rf .git`

This command will remove `.git` file from the directory. 

To confirm: 

`git status`

This will give a command of `fatal: Not a git repository (or any of the parent directories): .git`