---
title: 'Git Tips and Tricks'
date: 2025-04-19
lastmod: 2025-04-19

weight: 3

# Keywords help in classifying content
keywords:
  - Git Tips and Tricks
---

<!--more-->

The following are useful git tips and tricks.

## Cleanup to a given branch

Often times a git repo needs to be brought up-to-date with the remote quickly.  Using a feature branch style also means that branches need to be cleaned up as well.  The following does all that.

> [!INFO]
> If you copy the below into `git-cleanup` and put it in your path, then Git will automatically consider it a subcommand.  So within a git repo just run `git cleanup main` (note the space) will move your to the `main` branch, sync it with the remote, and delete any synced branches.

```bash
#!/usr/bin/env bash

# Unset the PAGER to prevent interactive behavior
unset PAGER

# Update main to remote, and branches that were deleted in the remote
# NOTE: "-d" will only delete if everything is merged, which doesn't work for
# squash commits.  so use "-D" instead

git fetch -p \
&& git checkout main \
&& git pull \
&& git branch -v | grep "\[gone\]" | awk '{print $1}' | xargs git branch -D

branch=$(git branch | grep "*" | awk '{print $2}')

if [[ "$branch" != "main" ]]; then
  echo "Left on branch $branch, manual cleanup may be required"
  git branch
  exit 1
fi
```

## Find the hash of the latest commit

```bash
# If you know you are in the HEAD commit
git rev-parse HEAD

# or, one that works regardless
git log --pretty="oneline" | head -n1 | awk '{print $1}'
```

## Find the files that changed

<aside>
💡 This works if you have a stable ancestor branch.

</aside>

```bash
ANCESTOR="master"
COMMMIT="HEAD" # replace with commit hash if you could be in detached head

# sync the acenstor branche to ensure it has full history
git fetch origin "$ANCESTOR:remotes/origin/$ANCESTOR"

# diff to the anscestor
git diff --name-only "origin/$ACTIVE_BRANCH"..."$COMMIT"

# Unfortunately this doesn't catch if you are on $ACTIVE_BRANCH.
# So you need to check the the last commit if the above produces no output
git diff --name-only "$COMMIT^..$COMMIT"
```
