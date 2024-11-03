# The differen between 'git pull' and 'git fetch'

In the simple terms, git pull does a git fetch followed by a git merge

Some Terms you should know:

* FETCH_HEAD: 一个版本链接，记录在本地的一个文件，指向目前已经从远程仓库拉取的分支的末端版本

* commit-id: 每次本地工作完成后，都会做一个git commit来保存当前工作到本地repo，此时会生成一个commit-id 这是一个唯一标识一个版本的序列号， 在git push 后这个序列号回同步到远程仓库