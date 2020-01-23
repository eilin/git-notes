# Git Notes
`"git gud, scrub"`

- [log format](#log-format)
- [aliases](#aliases)
- [selectively adding](#selectively-adding)
- [rebasing](#rebasing)
- [resolving merge conflicts](#resolving-merge-conflicts)
- [amending old commits](#amending-old-commits)


## Log Format
Format logs with options:
```
git log --pretty=oneline --abbrev-commit
```

Custom format:
```
git log --pretty="%h %d %s (%cr) [%an]"
```

Custom format with colors:
```
git log --pretty="%Cred%h%Creset %C(yellow)%d%Creset %s %Cgreen(%cr)%Creset %C(cyan)[%an]%Creset"
```

## Aliases
`git config --global alias.st status`

`git config --global alias.ll "log --pretty='%Cred%h%Creset %C(yellow)%d%Creset %s %Cgreen(%cr)%Creset %C(cyan)[%an]%Creset'"`

## Selectively Adding
`add -p` to enter "patch" mode to choose which hunks will be staged.

If a hunk needs to be split, use the `s` command. If the hunk cannot be split, use the `e` command to edit the patch context and add a "#" in front of the lines you don't want staged.


## Rebasing
TODO

## Resolving Merge Conflicts
Example of checkout theirs/ours:
> When merging branchA to branchB and you want to keep all changes from branchB for a specific file:  
`# branchB is checked out`  
`$ git merge branchA`  
`$ git checkout --ours file.txt`  
Here "--ours" refers to the version we have checked out, if we wanted to keep changes from branchA the option to use is "--theirs".

## Amending Old Commits
> **IMPORTANT** Never amend public commits as you will mess up other people's git histories.
### Amending HEAD
Add changes to index and use `commit --amend` (with `-C` option to accept existing message).

### Amending commits older than HEAD
Add change as new commit, then squash with old commit using interactive rebase. 

This can be done with the fixup and autosquash options.

1. Add change as new commit with `commit --fixup HASH`, where HASH is the hash of the old commit that you want to amend. This will create a new commit with the message "fixup! OLD_COMMIT_MSG".
2. Rebase with `rebase --autosquash --interactive` and git will know you want to squash the amendment from the "fixup!" in the commit message.
3. You should see your fixup commit reordered to be after the amend target in the interactive menu. Finish rebasing and the old commit should be changed.

## TODOs
rebasing (section and anchor exists)

rerere

git reset HEAD~N
--mixed (default mode) : updates index, not working copy
--soft : doesn't update index nor working copy
--hard : updates index and working copy

git aliases

interactive rebase edit the next commands using --edit-todo
resetting to before a interactive rebase based on the reflog
push --force-with-lease (a safer force push)
