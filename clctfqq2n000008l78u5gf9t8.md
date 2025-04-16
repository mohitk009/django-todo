---
title: "Git Commonly used commands"
seoTitle: "git cheatsheet in detail"
seoDescription: "git cheatsheet, git commands, git stash, git merge, git rebase"
datePublished: Wed Jan 11 2023 18:37:50 GMT+0000 (Coordinated Universal Time)
cuid: clctfqq2n000008l78u5gf9t8
slug: git-commonly-used-commands
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Uaf6XwW4n10/upload/153c27acb9459f801afa9a316e5f2f15.jpeg
tags: github, git, cheatsheet, git-commands, git-stash

---

## After setup / First Install

Using the setup option for various platforms we can install git on our system. We would be able to create local repo and track our files after this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673512317480/0ead0880-3e07-42ff-a884-67e514c8d141.png align="center")

`config --global` is used for configuring user information across all the repositories

## Setup & Init

Here, we go to [GitHub](https://www.github.com/) login to our account fork the repo of other user, using `<>Code`button we copy the url. After that on our local repo we initialize the empty repo and clone the remote repo to our local repo. Git would be able to track or untrack files after this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673512518168/88af6a88-0519-491d-92dc-f27c6d7ae312.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673512625548/642a31ec-ddc9-418f-88e7-ceca8271267d.png align="center")

## Stage and Snapshot

There are three type of storage area in git

1. **Working Dir (local area)**: In this area, files on our local file system are created, edited or deleted.
    
2. **Staging area**: In this area, changes before making a commit are visible. All the tracked file are in the staging area.
    
3. **Repository (remote area)**: In this area, after we use `git commit` and `git push` files get accessible on `github.com` and other users can contribute if repo access is public. All the metadata of git file and history of changes comes in this area.
    

There are some commands which we need to keep handy in order to get benefit from git.

| Git command | use of the command |
| --- | --- |
| `git status` | shows files which are being tracked and which are not |
| `git add [file]` | adds file to track the git changes |
| `git reset [file]` | remove the file from traking changes (staging) |
| `git diff` | changes between file when not tracked(unstage) |
| `git diff --staged` | changes between files staged but not committed |
| `git commit -m "<message>"` | when commiting a message is necessary |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673537174783/06385da9-5f43-4fa4-874e-b3b2d048ee51.png align="center")

Git status shows the untracked and tracked changes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673537300298/d2ad308b-9bc2-4b6b-b7db-f4511ec3fcc1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673537311159/57e39920-4cc6-4c2e-aba6-8eb08200ef1b.png align="center")

After performing `git reset <filename>` the file moves to untracked list from tracked list

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673537607858/eaca1c9d-3687-44d9-867e-7a1891caa078.png align="center")

`git diff` shows changes in untracked files while `git diff --staged` shows changes in tracked file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673537704052/b5159234-d64b-4fe9-8bda-7436216bca5e.png align="center")

`git commit -m <message>` generates hash id and adds the change to index. Here `git lo` is alias for `git log --oneline` HEAD points to latest commit id in master branch.

## Branch and Merge

From master branch we can make a its sub-branch and give it to the other person to work on any feature. According to branching & merging commands we can integrate the branches. Some common commands are

| Git command | Use Case |
| --- | --- |
| `git branch` | list the branches \* appears on current branch |
| `git branch <branch-name>` | a new branch is created with provided branch name |
| `git checkout` | switches to another branch and check it out into working dir |
| `git merge <branch>` | merges the branch into current |
| `git log` | shows hash id, date, commit message and author |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673538301392/174758b7-78e4-4075-ae75-b6e3037569e7.png align="center")

## Inspect and Compare

One of the feature of git is to track changes and perform useful operations related to these changes. Some of the commands related to this is shown below

| Git Command | Use Case |
| --- | --- |
| `git log --oneline` | shows the log in single line |
| `git log branchA..branchB` | shows commit on branchA not on branchB |
| `git log --follow <file>` | shows the commit that changed file, rename included |
| `git diff branchB...branchA` | show the diff of what is branchA not in branchB |
| `git show [SHA]` | show object in Git in human-readable format |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673538816361/eaac74e0-c887-4cc9-815e-0eb473479bb9.png align="center")

`git log` are shown in single line with commit id and branch, HEAD and message

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673538771770/4d23c34a-bb3c-4018-baad-02bec8d0972d.png align="center")

Author, Date, Hashid (commit id) , also `master` and `dev` branch are displayed seperately

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673538919884/2c2d7970-f29d-4b03-b6c7-94f9a15da4a7.png align="center")

There is a file `version01.txt` and using `git log --follow` the all the commits made to that particular file are being shown.

## Tracking Path Changes

The process of assigning hash-id (commit id) and keep track of file modifcation is called **versioning**. There are certain commands that help perform versioning in easier way.

| Git command | Use Case |
| --- | --- |
| `git rm <file>` | deletes the file from the project and stage (track) removal for commit |
| `git mv <existing-path> <new-path>` | to track file moved within the project |
| `git log --stat -M` | to list all commits that have moved path |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673539893350/be572929-3c1c-4204-a335-6940845e39a1.png align="center")

`git rm <filename>` deletes file and `git status` which tracks git repo shows the file that has been deleted

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673539969517/b260a941-fde6-4a6d-8735-5cdedb2ca100.png align="center")

`git stash` undo all the uncommited changes , `file` is recovered `git mv` moves fiel from one location to another. `git status` again shows that file has been moved.

## Ignoring Patterns

Sometimes we don't want our private data or large files to be kept on remote repository, for that git provides `.gitignore` file which helps to avoid storing specific file or files with certain pattern using wildcards. Some of the commonly used commands that ignore patterns are listed below.

| Git command | Use Case |
| --- | --- |
| `vim .gitignore` |  |
| logs/ |  |
| \*.notes |  |
| pattern\*/ | These patterns are inside `.gitignore` file, whenever these changes are commited git ignore these changes. |
| `git config --global core.excludesfile <filename>` | This command is used to define location of file that contains list of all the files/wildcards that has to be ignored |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673541098088/5109db95-12cd-4b68-9c15-403131b28013.png align="center")

First of all we created a `.gitignore` file and added a list of wildcards/file that git version control system need not track.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673541255262/e103638b-64e6-4c5a-b1e9-c560139f9aa7.png align="center")

Then we told the git about location of `.gitignore` file using `git config --global core.excludesfile <filename>` After that we added `feat1.txt` and `dev_file` and on checking status we noticed that file with `.txt` extension do not get added while the other one was added to staging area.

## Share and update

The git has some commands that are helpful for synchronisation between remote and local repository. These commands help in open source contribution, sharing code, or making changes in other person code.

| Git command | Use Case |
| --- | --- |
| `git remote add [alias] [url]` | add git url as alias |
| `git fetch` | fetches down all branches from git remote |
| `git merge [alias]/[branch]` | merge remote branch into current branch |
| `git push [alias] [branch]` | transmit local branch commit to the remote repo |
| `git pull` | fetch and merge any commit from tracking remote branch |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673542816759/4c6da33e-5221-4b6a-8b23-53a8eed58efd.png align="center")

The other developer created a branch `remote_branch` and pushed to git remote repo. Using `git fetch` our developer fetched the branch on local repo.

Using `git merge origin/remote_branch` our developer was able to merge remote branch with current branch.

`git fetch` has bought all the branches across the repo (remote/local) of multiple developers working on the project

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673545975334/e32c71fa-2a57-498f-83cb-708d6c594bda.png align="center")

it would push changes from `dev` branch to `origin` alias of remote repo as declared in previous command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673546007967/01e054b4-7257-45b9-9bb8-07cc7d1d0d89.png align="center")

`master` branch would pull changes from `origin/master` remote repository

## Rewrite History

Git has unique feature of retrieving deleted code /deleted feature that we wanted after removal. Because Git mantains a commit id which helps it to reset changes made.

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Git Command</strong></p></td><td colspan="1" rowspan="1"><p><strong>Use Case</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p><code>git rebase &lt;branch&gt;</code></p></td><td colspan="1" rowspan="1"><p>apply any commit of current branch ahead of &lt;branch&gt; specified</p></td></tr><tr><td colspan="1" rowspan="1"><p><code>git reset --hard &lt;commit&gt;</code></p></td><td colspan="1" rowspan="1"><p>clears staging area, rewrite working tree from specified commit</p></td></tr></tbody></table>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673547369811/6a3f885c-a22f-49e5-ac90-810a6a1bd9f9.png align="center")

`git log` shows that `test` branch is ahead of `dev` branch by two commits.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673547486781/d0206c0e-5f8f-41cc-aea9-4f54b33e7186.png align="center")

now, we `checkout` to `dev` branch and apply `git rebase` to test from dev branch. As evident from `git log` (alias: `git lo`) both branches point to same head.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673547663405/04ac76ab-850a-469d-9e02-5ab1962d7bcc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673547721114/c2ddcf3b-a1e7-45cf-8f32-bcb20b666961.png align="center")

we also see `git reset` in action. It has cleared particular commit using `commit id` and bought it to untracked state. `--hard` option deletes file if present after particular `commit id` mentioned.

## Temporary Commits

Git has a feature to stash save staged (tracked changes). It has certain command to facilitate this feature.

| Git Command | Use Case |
| --- | --- |
| `git stash` | save staged or tracked changes |
| `git stash list` | list of tracked or staged changes |
| `git stash pop` | inserts topmost change on the list to current repo |
| `git stash drop` | discards the changes from top of stash list |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673548241668/5785c082-6c2e-46c1-b951-9a207b957d1d.png align="center")

`git stash` in action. First we see untracked files with `git status` then we `git stash` to save our changes. After that we see the list of changes made using `git stash list`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673548368771/4bb845f7-a486-42fa-8b76-6fa9434d027e.png align="center")

`git stash pop` in action. After we `git stash` from `dev` branch we checked out to `test` branch where we used `git stash pop` to pop out topmost change in our stash list.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673548539215/b97215f2-9ac0-4768-ba3a-ae6a07b9da36.png align="center")

`git stash drop` in action. We see 3 items in stash list and we used `stash drop` then only 2 itmes were remaining in our stash list.

## References

[https://education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)

[https://www.trainwithshubham.com/](https://www.trainwithshubham.com/)