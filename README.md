# Git Notes
`"git gud, scrub"`

- [rebasing](#rebasing)
- [resolving merge conflicts](#resolving-merge-conflicts)

add -p

rerere

git reset HEAD~N
--mixed (default mode) : updates index, not working copy
--soft : doesn't update index nor working copy
--hard : updates index and working copy

amending commits
amending HEAD: add changes to index and use commit --amend (-C to accept same commit message)
amending commit older than head: add change as new commit and squash with old commit using interactive rebase

## Rebasing
interactive rebase --autosquash

## Resolving Merge Conflicts
resolve merge conflicts with --theirs / --ours