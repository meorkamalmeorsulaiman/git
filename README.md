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
user.email=kamal.sulaiman@paynet.my
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
