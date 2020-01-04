# git-notes
Simple snippets with brief explanation of git commands I find super-useful and use often.

---

- [How to delete a local branch](#to-delete-a-local-branch)

- [How to delete a remote branch](#to-delete-a-remote-branch)

- [How to remove remote origin from Git repository](#to-remove-remote-origin-from-git-repo)

- [How to update a Github forked repository](#to-update-a-github-forked-repository)

- [How to untrack a file by Git](#how-to-untrack-a-file-by-git)
  
- [How to untrack a directory by Git](#how-to-untrack-a-directory-by-git)

- [How to delete a .git folder from your project](#to-delete-a-git-folder-from-your-project)

- [How to change a remote's URL](#to-change-a-remote-url)

- [How to force push a git repo](#to-force-push-a-git-repo)

- [How to remove files from git that has been already been deleted from disk](#remove-files-from-git-that-have-already-been-deleted-from-disk)

---

#### To delete a local branch:
**N.B:You cannot delete the branch you are currently on.** 

If you are in the same branch that you want to delete, run:

`git checkout <another-branch>` to switch to another branch(because you can't delete a branch you are currently on)

Then delete the branch you want:

`git branch -d <branch-name>`

**NB:** If you haven't merged the branch you want to delete, you will get this error:

```
error: The branch 'slide' is not fully merged.
If you are sure you want to delete it, run 'git branch -D slide'.
```

To then force delete the branch that hasn't been merged yet:

`git branch -D <branch-name>`

---

#### To delete a remote branch:

`git push --delete <remote_name> <branch_name>`

---
#### To remove remote origin from Git repo:
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

#### How to untrack a file by git:

`git rm --cached <file path>`

---

#### How to untrack a directory by git:

To remove a file or folde already tracked by git, then you must first remove it (physically, file or folder must be placed out of git folder for the time), commit changes and add the file again to folder. Then git will begin ignoring it using your instruction. 

**Step 1:** Add the folder path to your repo's root `.gitignore` file.

**Step 2:** Remove the folder from your local git tracking, but keep it on your disk.

`git rm -r --cached <path_to_your_folder/>`

**Step 3:** Add, commit and push your changes to your git repo.

The folder will be considered "deleted" from Git's point of view (i.e. they are in past history, but not in the latest commit, and people pulling from this repo will get the files removed from their trees), but stay on your working directory because you've used --`cached`

---

#### To delete a git folder from your project:
`rm -rf .git`

This command will remove `.git` file from the directory. 

To confirm: 

`git status`

This will give a command of `fatal: Not a git repository (or any of the parent directories): .git`

---

#### To change a remote URL:

List your existing remote:

`git remote -v`

Then to change the existing to a new one:

`git remote set-url origin [URL]`

To confirm:

`git remote -v`

---

#### To force push a git repo:

`git push --force <origin_name> <your_branch_name>`

**Short flag**
Also note that `-f` is short for `--force`, so

`git push -f <origin_name> <your_branch_name>`

---

### Remove files from git that have already been deleted from disk


This tells git to automatically stage tracked files -- including deleting the previously tracked files.

To stage your whole working tree:

`git add -u :/`

To stage just the current path:

`git add -u .`

