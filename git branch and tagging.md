## Git Branch and tag

## git tag

[https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag](https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag)

A tag is like a branch that doesn't change, unlike branches, tag after being created, have no further history of commits

## create a tag

```
git tag <tagname>
```

## Pusshing tags to remote

```
git push origin v1.0
```

## Checking out tags

```
git checkout v1.4
```

the above command will checkout the v1.4 tag, this puts the repo in a detached HEAD state, this means any changes made will not update the tag, They will create a new detached commit, the detached commit will not be part of any branch and will only be reachable directly by the commit SHA hash.

therefore it is a best practise to create a new branch anytime you're making changes in a detached HEAD state

```
git checkout tags/v1.4 -b v1.4-branch

git push --set-upstream origin v1.0-branch           
```

the above command will checkout a tag and create a branch to it, and then push the new branch to remote
