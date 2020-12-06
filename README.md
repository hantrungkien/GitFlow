# GitFlow - to keeps linear or semi-linear git history cleaner and more readable.

### https://dev.to/scottshipp/war-of-the-git-flows-3ec2
### https://www.endoflineblog.com/oneflow-a-git-branching-model-and-workflow

* init

```
$ git init
$ git add .
$ git commit -m "init with README.md"
...
$ git commit --amend -m "change last commit message"
```

* create develop branch

```
$ git checkout -b develop master
$ git push --set-upstream origin develop
```

* create feature branch

```
$ git checkout -b feature/[feature_name] develop
$ git add .
$ git commit -m "[feature_name] message "
$ git push --set-upstream origin feature/[feature_name]
...
$ git pull --rebase
...
$ git rebase develop
...
$ git rebase -i HEAD~4 (last 4 commits)
$ git push --force-with-lease origin
```

* stash

```
$ git stash save
$ git stash list (-p to show all changes)
$ git stash show [stash_id]
$ git stash apply [stash_id]
$ git stash clear
```

* merge feature into develop

```
$ git checkout develop
$ git merge --no-ff feature/[feature_name] (semi-linear history)
$ git merge --ff-only feature/[feature_name] (linear history)
```

* create release branch

```
$ git checkout -b release/[version] develop
$ git tag [version]
```

* create hotfix branch

```
$ git checkout -b hotfix/[version] master
$ git tag [version]+1 (ex. 1.0.0+1)
```

* merge release/hotfix into master/develop

```
$ git checkout master
$ git merge --ff-only [release/[version] | hotfix/[version]]
$ git push origin --tag
```

```
$ git checkout develop
$ git merge --no-ff [release/[version] | hotfix/[version]] (semi-linear history)
$ git merge --ff-only [release/[version] | hotfix/[version]] (linear history)
```

