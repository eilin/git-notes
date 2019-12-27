# Git Notes
`"git gud, scrub"`

- [log format](#log-format)
- [selectively adding](#selectively-adding)
- [rebasing](#rebasing)
- [resolving merge conflicts](#resolving-merge-conflicts)
- [amending old commits](#amending-old-commits)

add -p

rerere

git reset HEAD~N
--mixed (default mode) : updates index, not working copy
--soft : doesn't update index nor working copy
--hard : updates index and working copy

amending commits
amending HEAD: add changes to index and use commit --amend (-C to accept same commit message)
amending commit older than head: add change as new commit and squash with old commit using interactive rebase

## Log Format
Format logs with options:
```
git log --pretty=oneline --abbrev-commit
28407e0 (HEAD -> master) amending and autosquash
cffef7d (origin/master) initial commit
```

Custom format:
```
git log --pretty="%h %d %s (%cr) [%an]"
```

Custom format with colors:
```
git log --pretty="%Cred%h%Creset %C(yellow)%d%Creset %s %Cgreen(%cr)%Creset %C(cyan)[%an]%Creset"
```
## Selectively Adding
`add -p` to enter "patch" mode to choose which hunks will be staged.

If a hunk needs to be split, use the `s` command. If the hunk cannot be split, use the `e` command to edit the patch context and add a "#" in front of the lines you don't want staged.


## Rebasing

## Resolving Merge Conflicts
resolve merge conflicts with --theirs / --ours

## Amending Old Commits

### Amending HEAD
Add changes to index and use `commit --amend` (with `-C` option to accept existing message).

### Amending commits older than HEAD
Add change as new commit, then squash with old commit using interactive rebase. 

This can be done with the fixup and autosquash options.

1. Add change as new commit with `commit --fixup HASH`, where HASH is the hash of the old commit that you want to amend. This will create a new commit with the message "fixup! OLD_COMMIT_MSG".
2. Rebase with `rebase --autosquash --interactive` and git will know you want to squash the amendment from the "fixup!" in the commit message.
