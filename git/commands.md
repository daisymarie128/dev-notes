### Useful commands

##### Merge specific
You can first run `git log` – to find the specific commit id you want to merge (it's the very long number)

Then to only merge that commit into the branch you want you return

`git cherry-pick [commit-id]`

This is useful if you've commited a few changes to the develop branch for example, and you don't want to push all those changes to the master branch just yet but you do have one important change that needs to happen. You can use this command.

##### Rename a branch
These commands will rename your branch you created both locally and remotley

```git
git branch -m old_branch new_branch         # Rename branch locally    
git push origin :old_branch                 # Delete the old branch    
git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote
```