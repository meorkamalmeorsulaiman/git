# git

This is where all the learning git's notes

## Requirements

- Ensure git install
- Validate git installed:

```bash
kamal@TS-Kamal:~/docker/lab/git/git$ git --version
git version 2.34.1
```

- Check configured username and email address that going to be use by Git:

```bash
kamal@TS-Kamal:~/docker/lab/git/git$ git config --list
user.name=Kamal Sulaiman
user.email=meorkamalmeorsulaiman@gmail.com
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=https://github.com/meorkamalmeorsulaiman/git.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.main.remote=origin
branch.main.merge=refs/heads/main
```

- Conifgure email and username:

```sh
($)git config --global user.email "meorkamameorsulaiman@gmail.com"
($)git config --global user.name "Kamal sulaiman"
```

## Start

- Create Git repo:

```sh
($) mkdir test-git
($) git init
```

- Change directory and go into the git repo `cd test-git`
- Create a file `touch test_file.txt`
- Check the git status:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git status
On branch lesson-3
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test_file.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

- File created has been staged but haven't commit
- Commit the created/edited files:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git add test_file.txt 
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git status
On branch lesson-3
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
        new file:   test_file.txt

kamal@TS-Kamal:~/docker/lab/git/kamal/git$ 
```

- The files is now included in a list of *changes to be commited*
- This mean, it has been added to the staging area but hasn't been committed yet
- Proceed to commit:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git commit --message="Update README.md and adding test_file.txt"
[lesson-3 3a664c8] Update README.md and adding test_file.txt
 2 files changed, 4 insertions(+), 4 deletions(-)
 create mode 100644 test_file.txt
```

- Validate with `git status` to ensure that every file edited has been stashed in the repository
- The commit contains many information as per below:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git log 
commit 3a664c8112e16b54573ada44764c2f7c788020d9 (HEAD -> lesson-3)
Author: Kamal Sulaiman <meorkamalmeorsulaiman@gmail.com>
Date:   Mon Jul 31 20:47:08 2023 +0800

    Update README.md and adding test_file.txt

commit 8b01b17b880440a9623dda8c1b8a3bdbe22f98f0 (origin/main, origin/HEAD, main)
Merge: f7fa5fa e8987a9
Author: meorkamalmeorsulaiman <81060743+meorkamalmeorsulaiman@users.noreply.github.com>
Date:   Mon Jul 31 20:24:27 2023 +0800

    Merge pull request #1 from meorkamalmeorsulaiman/lessson-1
    
    updating lesson 1 notes

commit e8987a911db80b405682340196e3a5018d6fcc28 (origin/lessson-1)
Author: Kamal Sulaiman <meorkamalmeorsulaiman@gmail.com>
Date:   Mon Jul 31 20:23:22 2023 +0800

    updating lesson 1 notes

commit f7fa5fa7e810ea2f19c4304aa635822f66416a11
Author: meorkamalmeorsulaiman <81060743+meorkamalmeorsulaiman@users.noreply.github.com>
Date:   Sun Jul 30 20:14:12 2023 +0800

    Initial commit
```

- Every commit will be hashed 

## Exclude files from the repository

- You can exclude file to be stashed in the repository
- Example items that could be added:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git status
On branch lesson-4
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .ide_config/
        personal-notes.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

- Solution, create a `.gitignore` in your root project's directory:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ cat .gitignore 
#personal notes
personal-notes.txt

#.ide_config directory
.ide_config/
```

- Validate the file won't be included:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git status
On branch lesson-4
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore

no changes added to commit (use "git add" and/or "git commit -a")
```

- Staged everything the into the repository:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git add *
The following paths are ignored by one of your .gitignore files:
personal-notes.txt
hint: Use -f if you really want to add them.
hint: Turn this message off by running
hint: "git config advice.addIgnoredFile false"
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git add .gitignore
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git status
On branch lesson-4
nothing to commit, working tree clean
```

- You will see that the content included in `.gitignore` would not be staged
- Proceed to stashed into the repository


```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git commit --message="adding ignore file and update README.md"
[lesson-4 7a5d06f] adding ignore file and update README.md
 1 file changed, 19 insertions(+), 1 deletion(-)
```

## Tagging

- You can tag particular commit
- *tags* help to identify which features has been deployed on production
- You must make sure to commit first and then later tag:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git add README.md 
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git commit -m "Update notes for tagging"
[lesson-5 8199fd2] Update notes for tagging
 1 file changed, 10 insertions(+)
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git tag version-1-0-tag
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git log
commit 8199fd23d2b1dac849b68fe8643aecd64e65b7da (HEAD -> lesson-5, tag: version-1-0-tag)
Author: Kamal Sulaiman <kamal.sulaiman@paynet.my>
Date:   Mon Jul 31 21:08:33 2023 +0800

    Update notes for tagging

commit b607acf976273d69977c516f5e3dc7809a340c6a (origin/main, origin/HEAD, main)
Merge: 4e0cef9 7c64fbb
Author: meorkamalmeorsulaiman <81060743+meorkamalmeorsulaiman@users.noreply.github.com>
Date:   Mon Jul 31 21:04:06 2023 +0800

    Merge pull request #4 from meorkamalmeorsulaiman/lesson-4
    
    Lesson 4

commit 7c64fbbc85eda943c6f31643e07470fe1e200ba5 (origin/lesson-4, lesson-4)
Author: Kamal Sulaiman <kamal.sulaiman@paynet.my>
Date:   Mon Jul 31 21:03:39 2023 +0800

    README.md was not stashed/commited

commit 7c7cf6cb16bf1ad26555fa0ced15aea8be2c8899
Author: Kamal Sulaiman <kamal.sulaiman@paynet.my>
Date:   Mon Jul 31 21:02:24 2023 +0800

    adding ignore file what was excluded

kamal@TS-Kamal:~/docker/lab/git/kamal/git$ 
```

- You can see the latest commit has been tagged
- I'm going to stage and stashed this change with different tag `version-1-1-tag`

## Branching codes

- Branch is just a series of ordered commits
- Branch create isolated work-space
- Later you can include the fixes into the main code that lives in main branch
- Method will be you create new branch and later fix within the newly created branch
- Once completed, merge with the main branch
- Example to create branch:

```bash
git branch [branch name]
```

- List available branch:

```bash
git branch
```

- Switch to different branch

```bash
git checkout [branch-name]
git switch [branch-name]
```

- Two command to merge from source *branch* to target *branch*:

```bash
git checkout main
git merge [source branch]
```

- Example merged branch of `lesson-6` to `main` *branch*:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git add README.md 
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git status
On branch lesson-6
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git commit --message="Adding notes for lesson-6"
[lesson-6 bc5e366] Adding notes for lesson-6
 1 file changed, 40 insertions(+), 1 deletion(-)
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git merge lesson-6
Updating 6684e1d..bc5e366
Fast-forward
 README.md | 41 ++++++++++++++++++++++++++++++++++++++++-
 1 file changed, 40 insertions(+), 1 deletion(-)
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git push origin main 
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 715 bytes | 715.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/meorkamalmeorsulaiman/git.git
   6684e1d..bc5e366  main -> main
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git pull
Already up to date.
```

- More branch commands:

```sh
$ git branch --delete [branch name] #delete branch
$ git branch --delete --force [branch-name] #delete with force, git will warn and will not delete if it haven't merge
```

## Syncing local and remote copies of repo

- When using git, the team must designated one of the repo as a *golden* repo
- That repo will be the latest and stable version of code base
- Every developer will edit the codes with their own fixes, it won't be officially part of the project's stable codes if it still put into the *golden* repository
- The workflow would be:
  - Developer *a* has new fixes
  - For developer *b* to get the new fix
  - Developer *a* need to push into golden repo
  - Then, developer *b* pull the branch from the golden repo
- To sync your repo with the *golden* repo, you need to know that the *golden* repo exists
- Any repo that is not in your local computer called *remote* repo
- There are 2 ways to get a repo onto your computer:
  - by `git init` or `git clone`
- `git clone` is the common to get remote repository
- 2 forms of cloning, **HTTPS** or **SSH**
- Example of cloning:

```bash
$ git clone git@github.com:meorkamalmeorsulaiman/git.git
$ git clone 
```

- Check the remote copy listed:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git remote --verbose
origin  https://github.com/meorkamalmeorsulaiman/git.git (fetch)
origin  https://github.com/meorkamalmeorsulaiman/git.git (push)
```

- fetch is to get others commits
- push is sending your commits
- Noticed the word *origin*, it is to refer the golden repository which it the remote repo

## Pushing

- *push* is a term for send
- It's a process of copying your local commits to the *golden* repo
- To *push* you must make sure that you are in the branch you want to *push*, and then *push* it
- For the first time, you need to tell the remote repo what to nate the copy of your branch
- The remote copy of your branch in the *golden* repo is informally called the *upstream* branch
- You need to switch to the local branch and pass a few extra options to `git push`
- Example:

```bash
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git status
On branch lesson-7
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git commit -m "Adding notes for lesson-7"
[lesson-7 90e6fb4] Adding notes for lesson-7
 1 file changed, 46 insertions(+), 1 deletion(-)
kamal@TS-Kamal:~/docker/lab/git/kamal/git$ git push --set-upstream origin lesson-7 
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 1.18 KiB | 1.18 MiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'lesson-7' on GitHub by visiting:
remote:      https://github.com/meorkamalmeorsulaiman/git/pull/new/lesson-7
remote: 
```
