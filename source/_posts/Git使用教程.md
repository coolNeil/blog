---
title: Git使用教程
date: 2017-04-26 23:07:43
categories:
  - Tools
tags:
  - Git
comments: false
---

## 安装及初始化配置
安装的话，下载好软件直接一路下一步就行了。然后执行以下命令：
`git config  --global user.name "xxx"`
`git config  --global user.email "xxx"`
查看配置信息：`git config --list`

## 创建版本库
在项目目录下执行`git init`命令，创建一个版本库
![](/images/git-status.png)
上图包含三个区：工作区，暂存区，本地仓库
将文件添加到版本库：

  + `git add .`  (.表示工作区中所有的已修改的文件) 添加到暂存区
  + `git commit -m "xxx"` 提交到仓库
  + `git commit -am "xxx"` 一次性提交到代码库（注意对新创建的文件无效）
  + `git commit --amend` 可以重新写提交信息。如果有文件忘了commit了，可以在commit之后，再add一下，再运行`git commit --amend`

`git status` 可以查看状态
`git diff index.html` 比较工作区与暂存区的文件差异
`git diff --cached` 比较暂存区与上次提交的快照之间的差异

## 撤销修改和删除文件
未commit之前，发现写错了
+ 手动修改，然后add，再commit
+ `git reset --hard HEAD^`
+ `git checkout -- index.html` 丢弃**工作区**的修改，如果已经add进暂存区了，则无效

删除了文件，但是未commit，可以这样挽救：
`git checkout -- index.html`

手动删除了文件，比如`rm index.html`,运行 `git status` 时就会在 “Changes not staged for commit” 部分（也就是未暂存清单）,这个时候运行`git rm index.html`就好了


## 版本回退
`git log` 查看日志
`git log --oneline` 查看简洁日志
`git reflog` 查看所有分支的所有记录
`git reset --hard HEAD^` 或者 `git reset --hard HEAD~0` 回退到上一次commit时的状态
`git reset --hard 版本号` 回退到指定版本

## 远程仓库

### 创建远程仓库
+ 生成SSH Key：`ssh-keygen  -t rsa –C "youremail@example.com"`,并将公钥添加至github账号中
+ `git remote add origin git@github.com:coolNeil/test.git`
+ `git push -u origin master` 将本地分支的master与远程的master进行关联，这样以后就可以只执行`git push`命令将代码上传至服务器了

### 从远程仓库克隆
+ `git clone git@github.com:coolNeil/test.git`

## 创建与合并分支
+ `git branch` 查看分支
+ `git branch dev` 创建dev分支
+ `git checkout dev` 切换dev分支
+ `git checkout -b dev` 创建并切换dev分支
+ `git merge dev` 合并指定分支dev到当前分支（注意这样合并是Fast Forward模式，合并是直接把master指向dev的当前提交，也就是master分支和dev分支都指向相同的提交对象。当删除分支后，分支上的信息会丢掉，如果不想这样，可以使用--no-ff参数禁用Fast Forward模式）
  - 在分支上add一次
  - `git checkout master`
  - `git merge --no-ff -m "禁用FF合并分支" dev`
  - `git branch -d dev`
  - `git log --graph --pretty=oneline --abbrev-commit`发现删除的分支信息还在
+ `git branch -d dev` 删除dev分支

## bug分支处理
如果你在dev分支上开发，突然叫你去处理一个bug，这个时候由于你功能并没有做完，不能提交，你可以将dev分支stash一下，此时dev分支就是干净的了，然后去到那个将要修复bug的分支创建分支开始修复bug，修复完了之后，再回到dev分支，使用`git stash pop`
+ `git stash`将当前的工作现场隐藏起来 等以后恢复现场后继续工作
+ `git stash list` 查看所有被隐藏的文件列表
+ `git stash apply` 恢复，恢复后，stash内容并不删除，你需要使用命令git stash drop来删除
+ `git stash drop` 删除文件
+ `git stash pop` 恢复的同时把stash内容也删除了

## 多人协作

### 推送分支
`git push origin master` 想要推送到哪个分支，就写哪个分支，一些bug分支需要先合并到主分支，然后再推送到远程去

### 抓取分支
现有这种情况，如果你同事想要再dev分支上做开发，那么他应该这样做：
+ `git clone git@github.com:coolNeil/test.git`
+ `git checkout  –b dev origin/dev` 创建远程origin的dev分支到本地来

如果这个时候，你在dev分支上作了修改，并且和你同事是在相同的地方，那么你在push的时候会报错，这个时候，你应该现pull一下。如果pull也报错了，那么原因多半是没有指定本地dev分支与远程origin/dev分支的链接，此时应该先`git branch --set-upstream dev origin/dev`,再pull成功之后，手动解决掉冲突就可以push了。


## 标签
+ `git tag`显示标签
+ `git tag v1.0` 新建tag
+ `git tag -a v1.0 -m "my version v1.0"` 含附注的tag
+ `git show v1.0`显示tag
+ `git push origin v1.0`或`git push origin --tags` 分享标签