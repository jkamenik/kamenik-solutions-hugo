---
title: 'Gitflow Simple'
date: 2016-02-02
lastmod: 2016-02-02

# Keywords help in classifying content
keywords:
  - Gitflow Simple
  - Gitflow
  - Git
  - Process
  - How To
---

[Gitflow](http://nvie.com/posts/a-successful-git-branching-model/) is a great workflow to ensure you maintain constant ever increasing version numbers with enough room to fix mistakes. The downside is the slowness of deploying new features. GitFlowSimple is a simplified version which can be expanded to standard GitFlow when needed, but is less effort when deploying new features.

<!--more-->

## Assumptions

This method assumes the following are true:

1. You understand the following features of git
    1. How to branch from a non-HEAD commit
    1. How to deal with a merge conflict
    1. That linear history is an illusion (so you use `git log -a --graph`).
1. You understand what is meant by a "SNAPSHOT" version.
    1. Basically, ever changing code which devs can use, but never goes into production.
1. You have read and understand GitFlow
1. You need to release changes quickly.
    1. For example, you are maintaining several projects and need to add features to a library package; GitFlowSimple is ideal for the library.
1. You don't care about contiguous version numbers.
    1. they The numbers are ever increasing, but may not be in sequence (a use might get 1.2.5 as the update to 1.1.0).

This branching style is ideal for library code that is not normally seen by an end user, or end-user software that is automatically updated since the end-user doesn't usually keep track of version numbers. You mileage may vary, and you can always migrate to the standard GitFlow workflow when needed.

## Branching

Where GitFlow has "develop", "master", feature, release, and hotfix branches, GitFlowSimple only has "master", and feature branches (or you can call them release branches if you like merging several features into a release). Everything that is done on the extra GitFlow branches is be done directly on a feature branch or master branch in GitFlowSimple.

## The main branch

"master" is the only main branch and (just like GitFlow) it must remain production ready. And just like GitFlow this is the branch where version tags are created.

Unlike GitFlow this is also the branch where version numbers are bumped. The flow looks a little bit like this:

1. HEAD is version 1.0 (which is also tagged)
2. A feature branch is created from the HEAD commit of master
3. The feature is bumped into a snapshot image as follows:
    1. The version file (inside the source code) is updated to 1.1.0-SNAPSHOT
    1. The change is committed, immediately
    1. The change and the feature branch are pushed to the central repo
    1. The feature is developed
    1. The feature is tested and merged (`git merge --no-ff`)
9. On master, the version is bumped as follows:
    1. The Version file is updated to 1.1.0 (no "-SNAPSHOT")
    1. The change is committed
    1. The change is tagged
    1. All changes are pushed to the central repo

Merging using `--no-ff` prevents git from linear-izing the commits and makes it easy (using `git log -a --graph`) to see all the branches/features.

## Supporting Branches

The hotfix and feature branches are both used in GitFlowSimple. The two branches serve the same purpose as they do in GitFlow. The release branch serves no function in GitFlowSimple.

## An example

GitFlowSimple is best shown using an example. Lets assume the project is currently at 1.0, and a defect that popped up needs to be fixed, and at the same time two new features need to be added. I am going to deal with each in turn, but in actuality they will be done in parallel.

### Hotfix

1. A hotfix branch is created using the 1.0 tag (unlike GitFlow which would have used the "master" branch for this). The branch is called "hotfix-1.0.1".
2. The version file is updated to "1.0.1-SNAPSHOT" and committed.
3. The branch is pushed
4. The defect is fixed (which takes 10 commits)
5. The defect is tested

Now we need to merge to master and claim the rightful version number.

1. The code is merged to master
2. On master the version is updated to "1.0.1"
3. The change is committed
4. The commit is tagged "1.0.1"
5. The commit and tag are pushed to origin

### Feature 1

Started at the same time as the Hotfix.

1. A feature branch is created using master's HEAD (currently 1.0.0) is created named "feature-1".
2. The version file is updated to "1.1.0-SNAPSHOT" and committed.
3. The branch is pushed
4. The feature is added (which takes 3 commits)

Now we need to merge to "master" and create a release, but the Hotfix was already merged.

1. The code is merged to master, but fails because of a version file conflict
2. The merge is reverted.
3. The feature branch is checked out and "master" is merged back into the feature branch.
4. The conflict is present again. It is fixed by keeping our "1.1.0-SNAPSHOT" version. Note: we did this because our version was greater then what was in master; see "Feature 2" for what to do when this is not the case.
5. We retest before merging to master.
6. We attempt the merge to master again. There are no conflicts so we bump the version number as we did with the Hotfix; becoming 1.1.0.

### Feature 2

Feature 2 logically started on the 0.9 version so has the 1.0.0-SNAPSHOT version. This feature is not finished until after feature 1 has been merged.

1. Master has been pulled
2. Master is merged into the feature branch, with a conflict on the version file.
3. The conflict is fixed by keeping master's version: 1.1.0.
4. The version number is bumped to 1.2.0-SNAPSHOT (as if this was a new branch based on the current master)
5. The code is retested
6. The branch is merged into master (as with feature 1 and the hotfix becoming 1.2.0.

#### Multiple Same Versions

There is a chance when merging a feature it will not create a merge conflict because it is trying to claim the same version as what is already in master.

This is why it is important to **ALWAYS** do the following when merging features:

1. Merge master back into the feature branch before merging the feature into master.
2. Manually update the version number if no merge conflict happened.
