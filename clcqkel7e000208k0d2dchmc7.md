---
title: "Git Advance Concepts"
datePublished: Tue Jan 10 2023 18:27:07 GMT+0000 (Coordinated Universal Time)
cuid: clcqkel7e000208k0d2dchmc7
slug: git-advance-concepts
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/wX2L8L-fGeA/upload/8f25808c29d596251fcf37473e0d7162.jpeg
tags: github, git, advanced-git, merge-conflict

---

branching, restore, reset, reverting, cherry-picking, stashing, squashing, rebasing, merging

Git becomes a lot more interesting when we know about its advanced features. Everyone knows about basic git features which are used in routine but sometimes we encounter situations like collaboration with other people, changes in client requirements, the addition of new features, and rolling back to old features where advanced concepts in git are used.

## Branching

Branching creates a new branch to experiment without disrupting the main branch where the code resides. Let's understand by jumping into the shell.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673171669577/c11743cb-18ec-4135-a039-7cb83a0ba4ce.png align="center")

The command `git checkout -b new_branch` would simply create a new branch. We can see a list of already created branches using `git branch` In the given screenshot, we can see all the existing branches.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673171756385/0f1a979c-bedf-40be-aa0c-54747be0ddfe.png align="center")

Now we switch to the existing `dev` branch using `git checkout dev` and create, add and commit file `dev_file.txt` as shown in screenshot given below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673172016306/0adeb3b6-08f6-4a83-91d4-fade9a53b770.png align="center")

After this, we check the `git log --oneline` to display **hash id** and **commit message.** We also check current **HEAD** points to the dev branch as shown below. We also know that it is on the local repo branch as HEAD is pointing to **dev** and not to the **origin/dev** which is the remote repo branch. After we push the code only then HEAD would point to **origin/dev**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673172163512/f7f559d7-06a1-4655-b7b0-1ae919e2ca97.png align="center")

What would happen when we create another branch from the dev branch? Where would it's a head point to?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673174082197/2163d3bb-d98d-416d-a641-167b4fc2aabb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673174101042/1ec5d62a-074f-4a99-b6f4-142f0b378bbe.png align="center")

As it is evident from the above screenshot, the sub-branch `feat/enhanced_dev` is created and HEAD points to its parent `dev` and itself `feat/enhanced_dev` branch.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673174721013/09125fc1-7e8b-4c0f-b29a-ac2808d0c459.png align="center")

## Restore, revert and reset

First, we check if we have made any commits or not using `git status` command after making the required changes to the file. The following command would show an untracked file. If we add files to git using `git add <filename>` we have our files in the staging area. We can only use `git restore` command in the staging area (after git add) while `git revert` is used when we want to revert the committed file (after git commit).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673175770453/bfdeadc8-482d-4687-a4e3-12651fd28122.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673175799270/02bc3f89-69a2-4de0-8781-1ae113f8a84d.png align="center")

After we add the file2 to the staging area, with the help of the `git restore` the command we bring it to the previous state.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673176484669/2717b256-4dec-4abc-9bed-8001a6f39799.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673176573290/6b71e2bb-1bff-42ad-91ef-14a239434e17.png align="center")

From the `git log` it is evident that after commiting files in folder and using it's commit hash id we were able to revert the whole folder existing in branch feat/enhanced\_dev

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673178319405/49a2ff8d-adbd-4dac-93dd-58845c7fda90.png align="center")

Now, if we want to reset to some past commit we use `git reset --soft <commit-id>` Then using `git log --oneline` we check the HEAD and find that it points to the same commit-id we mentioned in `reset` command. The `--soft` option does not delete file from local repo while `--hard` option permanently delete file and usually not recommended to use. Given below is output of `git log --oneline` and current HEAD points to same hash-id mentioned in above screenshot.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673178586790/c00dfbf7-7ac9-4801-9646-4cb2fffca93d.png align="center")

## Cherry Picking

It is a process in which commits from other branch can be bought to our current branch. We should know hash id of the commit we are going to cherry pick into the current branch.

[![cherry-pick (stack overflow)](https://cdn.hashnode.com/res/hashnode/image/upload/v1673367428229/76484954-0437-49e1-be00-bcacc73df148.gif align="center")](https://stackoverflow.com/questions/9339429/what-does-cherry-picking-a-commit-with-git-mean)

Let's say, we have two branches `rec` and `dev` and we will cherry pick one commit of **rec into the branch dev.**

1. A file `rec_branch_file` is added and commited in rec branch. Note the hash id of commit **51dbd11**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673367121068/531f8986-7d19-4bcf-9183-1a00f6a788d0.png align="center")
    
2. Now just checkout to dev branch and enter `git cherry-pick 51dbd11` and voila, same file is created on `dev` branch
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673367324978/25d836a6-4c84-401a-ab8f-544077a28794.png align="center")
    

## Stashing

This is used to save changes in local repo and keep them aside before moving them to staging area. Once we are back to current branch after switching to other branch , we can revert changes in local repo.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673369989103/6c21d6b9-617f-4a7f-9c0c-ed6148397786.png align="center")

1. Make the required changes in your branch ie. create, remove, update or delete any content in file
    
2. Use `git stash` to save the changes to **stash list**. We may use `git stash -u` to add any untracked changes to our **stash list.**
    
3. We can use `git stash list` to show the changes saved in stash list. To apply the changes after coming back from other branch we can use `git stash apply <stash- list-number>`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673370926626/45f1a078-2262-4b09-9d23-f5a6c30f3cc6.png align="center")
    

## What are merge conflict and how to resolve?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673365372930/6bd17d2a-6cea-40e9-bbdb-308d497b4326.png align="center")

Merge conflict occur when two or more developer are working on the same file but have different code. Let's understand with example.

1. Dev 1 creates a file on local repo, moves it to staging area with `git add <filename>` and commits file with `git commit -m <msg>` command.
    
2. Another Dev 2 pulls the code from same repo. Then it modifies the same file, make some changes and pushes changes to the remote using `git push orign <branchname>`
    
3. Dev 1 comes next day, pulls the remote repo using `git pull origin <branchname>` he finds **merge conflict**
    
4. To resolve merge conflict there are four options as shown in above screenshot.
    
    a. Accept Current Changes: This will keep the local changes or current branch changes.
    
    b. Accept Incoming Changes: This will keep the remote branch changes or merged branch changes.
    
    c. Accept Both Changes: Keeps the both local/current and remote/merged branch changes.
    
5. After resolving, Dev 1 needs to add and commit the changes. Then he needs to push the changes to remote repo so that further conflicts do not occur.
    

## Merge Conflict while merging two branches

We can also see conflicts happening while merging two branches. Let's say we have `my_branch` and `his_branch`

1. We can clearly see **my\_branch** has 4 items while **his\_branch** has 6 items. Confict can happen at line 4 as it is common in both branches.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673368545498/53c7f172-b185-40b0-afca-9ec3d1f118f4.png align="center")
    
2. Now **my\_branch (current\_branch)** wants to merge features of **his\_branch (branch\_to\_be\_merged)** by first `git checkout <current_branch>` and then `git merge <branch_to_be_merged>`
    
3. As soon as branch gets merged, conflict occurs.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673368924706/da49308d-73ff-46a7-8de4-82dab214ff49.png align="center")
    

## Merge Vs Rebase

In the following screenshot, Merge would simply ignore commits in `dev` branch while rebase would include(overwrite) commits in `dev` branch to `main` branch.

1. Rebase is preferred in local branches and shouldn't be performed on master/main branch
    
2. If done accidently on master branch, rebase can be undo with the help of `git reflog`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673372338630/f18a7fa2-0d26-482f-9c00-e8a9a7ae2502.png align="center")

1. We have two branches `branch1` and `branch2` which have some commits in them.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673374083010/6eda281b-123b-4238-bc10-909e296ab256.png align="center")
    
2. What `git rebase -i <branch2>` does after `git checkout <branch1>` is, it would show which commits to include in rebase. After saving in editor rebase would be applied and commits from branch1 and branch2 would be displayed.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673374857305/1c0588f8-8c18-4f7c-bb50-579e39be0ab9.png align="center")
    
3. Here, picked commits have been applied. Since they were causing merge conflict, this would have to be resolved manually.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673374998445/447bd8af-172c-4e3e-8e8a-bd26ecbd74f1.png align="center")
    

This was bit lengthy blog on advance git concepts but when hands on these concepts are applied understanding about them gets better.

Keep learning, keep giving feedback about blog.

## References

1. [https://www.trainwithshubham.com/](https://www.trainwithshubham.com/)
    
2. [https://www.youtube.com/@Ihatetomatoes](https://www.youtube.com/@Ihatetomatoes)