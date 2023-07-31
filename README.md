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