# Git demo

This are some oprational procedures with git

## Seting up the config 

Several common config require
 - Name
 - Email

To see the current config on your get use can use command as below in GIT Bash

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github
$ git -v
git version 2.49.0.windows.1

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=schannel
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
user.email=meorkamil97@gmail.com
```

Let's set the name and email

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github
$ git config --global user.email "meorkamalmeorsulaiman@gmail.com"

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github
$ git config --global user.name "Kamal Sulaiman"
```

Now, validate the settings

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=schannel
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
user.email=meorkamalmeorsulaiman@gmail.com
user.name=Kamal Sulaiman
```

## Download repository to local machine

Think of repository as a directory contain all the files. You will be working on that directory and the first steps is to download the directory or repository. Below shows how you can download a repository

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github
$ git clone https://github.com/meorkamalmeorsulaiman/git.git
Cloning into 'git'...
remote: Enumerating objects: 83, done.
remote: Counting objects: 100% (83/83), done.
remote: Compressing objects: 100% (63/63), done.
remote: Total 83 (delta 20), reused 58 (delta 16), pack-reused 0 (from 0)
Receiving objects: 100% (83/83), 25.69 KiB | 797.00 KiB/s, done.
Resolving deltas: 100% (20/20), done.

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github
$ ls
git/
```

Above you can see the have clone the repo and one folder exist which is the repository downloaded or clone. Now let go and look at what are there

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github
$ cd git/

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (main)
$ ls
README.md  test_file.txt
```
## Branch

Now there are few file, now let see what branch is. Below we can see only one branch which is `main`

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (main)
$ git branch
* main
```
`main` branch is where all the finalized files or codes that we have created. Finalized mean it is tested, validated and working codes. At this point, I will create or push a branch to create this demo documents. 

Now we update our local repo to get the latest updates

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (main)
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (4/4), 2.13 KiB | 57.00 KiB/s, done.
From https://github.com/meorkamalmeorsulaiman/git
 * [new branch]      meorkamalmeorsulaiman-part-1 -> origin/meorkamalmeorsulaiman-part-1
Already up to date.
```

Above we can see the new branch called `meorkamalmeorsulaiman-part-1`. Let's switch to that branch. Below we can see the is a new folder inside the new branch - `part-1`

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (main)
$ git checkout meorkamalmeorsulaiman-part-1
branch 'meorkamalmeorsulaiman-part-1' set up to track 'origin/meorkamalmeorsulaiman-part-1'.
Switched to a new branch 'meorkamalmeorsulaiman-part-1'

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (meorkamalmeorsulaiman-part-1)
$ ls
README.md  part-1/  test_file.txt
```

If we switch back to the `main` branch and the new folder doesn't exist

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (meorkamalmeorsulaiman-part-1)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (main)
$ ls
README.md  test_file.txt
```

So, branch in general is a folder where you can introduce new codes without messing up the finalized codes in the `main` branch.

## Editing file in branch

Let's create a new branch for our new codes

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (main)
$ git checkout -b merkamalmeorsulaiman-demo
Switched to a new branch 'merkamalmeorsulaiman-demo'

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ git branch
  main
* merkamalmeorsulaiman-demo
```

Let's see create a file inside this `demo` branch
```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ touch test_file_1.txt
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ ls
README.md  test_file.txt  test_file_1.txt

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ git status
On branch merkamalmeorsulaiman-demo
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test_file_1.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Git will always keep track all the content in the branch. We created `test_file_1.txt` and git noticed it. What we can do is to stage the file

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ git add test_file_1.txt

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ git status
On branch merkamalmeorsulaiman-demo
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   test_file_1.txt
```

We have `add` the new file which put it into temporary container, git also noticed that it should be commited. Commit mean save all the changes what we have staged. Let's commit the changes

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ git commit -m "adding new files"
[merkamalmeorsulaiman-demo dc183e2] adding new files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test_file_1.txt

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ git status
On branch merkamalmeorsulaiman-demo
nothing to commit, working tree clean
```

Now we all saved the changes and then we can push to the origin branch. Origin mean the source of the repository. In this case the source should be the url that we use to clone this reposity

```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ git push -u origin merkamalmeorsulaiman-demo
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 255 bytes | 255.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'merkamalmeorsulaiman-demo' on GitHub by visiting:
remote:      https://github.com/meorkamalmeorsulaiman/git/pull/new/merkamalmeorsulaiman-demo
remote:
To https://github.com/meorkamalmeorsulaiman/git.git
 * [new branch]      merkamalmeorsulaiman-demo -> merkamalmeorsulaiman-demo
branch 'merkamalmeorsulaiman-demo' set up to track 'origin/merkamalmeorsulaiman-demo'.
```

## Pull Request

Now, we have create a pull request. Pull request in general is a change that we have propose. So this proposed change will then merge into the `main` branch. Here is the link to `demo` pull request [Demo Branch Pull Request](https://github.com/meorkamalmeorsulaiman/git/pull/14) If we dont have any conflicting codes then we can proceed to merged it into `main` branch. Let's proceed to merge it. This is done on the gui. If you check the pull request link it will shows that it has been merged. 

Now we have to update our local repo so that we get the updated codes. Below we switch to `main` branch all get all the update using `pull` feature
```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (merkamalmeorsulaiman-demo)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (main)
$ git pull
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (5/5), 2.38 KiB | 87.00 KiB/s, done.
From https://github.com/meorkamalmeorsulaiman/git
   ad462ef..db55d23  main       -> origin/main
   b3c938e..a725ef6  meorkamalmeorsulaiman-part-1 -> origin/meorkamalmeorsulaiman-part-1
Updating ad462ef..db55d23
Fast-forward
 test_file_1.txt | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test_file_1.txt
```

Now we can see our new file included in the `main` branch
```
MK97@DESKTOP-B1EU7E6 MINGW64 ~/Documents/github/git (main)
$ ls
README.md  test_file.txt  test_file_1.txt
```

