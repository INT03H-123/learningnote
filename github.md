# github的使用
## 从github上克隆仓库到本地
```c
git clone 远程仓库地址
git  add * //将修改的文件添加到暂存
git commit -m "提交备注" //将文件推送到本地版本库
git push origin master 或者 git push  //执行远程推送
```

## 从本地修改上传到远程仓库
```c++
git add 文件名 //将要上传的文件添加到暂存
git  add .  //将目录下的所有文件添加到暂存
git commit -m "提交备注" //将文件推送到本地版本库
git  push origin master 或者git push //
```

## 删除github中的某个文件或文件夹
在Github上我们只能删除仓库，并不能删除文件或者文件夹，所以只能用命令来解决。
1. 本地仓库和远程仓库同时删除
```cpp
 //先在本地上把两个文件删除，然后执行以下命令
 git add * //把本地仓库的文件上传到缓存。
 git commit -m 'del' //把第一步上传到缓存的东西上传到本地仓库，其中'del'是操作标识，内容随便填，方便用户观看。
 git push origin master //把本地仓库的文件上传到远程仓库。
```
2. 只删除远程仓库，不删除本地仓库
```cpp
 git pull origin master //将远程仓库里面的项目拉下来。
 dir  //显示本地目录下的文件
 git rm -r --cached 删除文件的文件名 //将此文件添加到暂存
 git commit -m  ‘删除了这个文件’ //
 git push -u origin master //把
```

git status //查看状态
将本地库的内容推送到远程，使用git push命令
实际上把当前分支master推送到远程

## 新建代码库
```cpp
# 在当前目录新建一个Git代码库
 git init
# 新建一个目录，将其初始化为Git代码库
 git init [project-name]
# 下载一个项目和它的整个代码历史
 git clone [url]
```
 
## 配置
```cpp

# 显示当前的Git配置
 
$ git config --list
 
# 编辑Git配置文件
 
$ git config -e [--global]
 
# 设置提交代码时的用户信息
 
$ git config [--global] user.name "[name]"
 
$ git config [--global] user.email "[email address]"
```

## 增加/删除文件
```cpp

# 添加指定文件到暂存区 
$ git add [file1] [file2] ...
 
# 添加指定目录到暂存区，包括子目录 
$ git add [dir] 
 
# 添加当前目录的所有文件到暂存区
$ git add .
 
# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交 
$ git add -p
 
 
# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...
 
# 停止追踪指定文件，但该文件会保留在工作区 
$ git rm --cached [file]
 
# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]
```

## 代码提交
```cpp

# 提交暂存区到仓库区
$ git commit -m [message]
 
# 提交暂存区的指定文件到仓库区 
$ git commit [file1] [file2] ... -m [message]
  
# 提交工作区自上次commit之后的变化，直接到仓库区 
$ git commit -a
  
# 提交时显示所有diff信息 
$ git commit -v
  
# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]
 
# 重做上一次commit，并包括指定文件的新变化 
$ git commit --amend [file1] [file2] ...
``` 

## 代码提交
```cpp
# 提交暂存区到仓库区
$ git commit -m [message]
 
# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]
 
# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a
 
# 提交时显示所有diff信息 
$ git commit -v
  
# 使用一次新的commit，替代上一次提交 
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息 
$ git commit --amend -m [message]
 
# 重做上一次commit，并包括指定文件的新变化 
$ git commit --amend [file1] [file2] ...
```

## 分支
```cpp
# 列出所有本地分支
$ git branch
 
# 列出所有远程分支
$ git branch -r
 
# 列出所有本地分支和远程分支
$ git branch -a
 
# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]
 
# 新建一个分支，并切换到该分支
$ git checkout -b [branch]
 
# 新建一个分支，指向指定commit
$ git branch [branch] [commit]
 
# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]
 
# 切换到指定分支，并更新工作区
$ git checkout [branch-name]
 
# 切换到上一个分支
$ git checkout -
 
# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]
 
# 合并指定分支到当前分支
$ git merge [branch]
 
# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]
 
# 删除分支
$ git branch -d [branch-name]
 
# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```
## 标签
```cpp
# 列出所有tag
$ git tag
 
# 新建一个tag在当前commit
$ git tag [tag]
 
# 新建一个tag在指定commit 
$ git tag [tag] [commit]
 
# 删除本地tag
$ git tag -d [tag]
 
# 删除远程tag
$ git push origin :refs/tags/[tagName]
 
# 查看tag信息
$ git show [tag]
 
# 提交指定tag
$ git push [remote] [tag]
  
# 提交所有tag 
$ git push [remote] --tags
 
# 新建一个分支，指向某个tag 
$ git checkout -b [branch] [tag]
```
## 查看信息
```cpp
# 显示有变更的文件
$ git status
 
# 显示当前分支的版本历史
$ git log
 
# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat
 
# 搜索提交历史，根据关键词
$ git log -S [keyword]
 
# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s
 
# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature
 
# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]
 
# 显示指定文件相关的每一次diff
$ git log -p [file]
 
# 显示过去5次提交
$ git log -5 --pretty --oneline
 
# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn
 
# 显示指定文件是什么人在什么时间修改过
$ git blame [file]
 
# 显示暂存区和工作区的差异
$ git diff
 
# 显示暂存区和上一个commit的差异
$ git diff --cached [file]
 
# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD
 
# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]
 
# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"
 
# 显示某次提交的元数据和内容变化
$ git show [commit]
 
# 显示某次提交发生变化的文件
$ git show --name-only [commit]
 
# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]
 
# 显示当前分支的最近几次提交
$ git reflog
```

## 远程同步
```cpp
# 下载远程仓库的所有变动
$ git fetch [remote]
 
# 显示所有远程仓库
$ git remote -v
 
# 显示某个远程仓库的信息
$ git remote show [remote]
 
# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]
 
# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]
 
# 上传本地指定分支到远程仓库
$ git push [remote] [branch]
 
# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force
 
# 推送所有分支到远程仓库
$ git push [remote] --all
```

## 撤销
```cpp
# 恢复暂存区的指定文件到工作区
$ git checkout [file]
 
# 恢复某个commit的指定文件到暂存区和工作区 
$ git checkout [commit] [file]
 
# 恢复暂存区的所有文件到工作区 
$ git checkout .
 
# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]
 
# 重置暂存区与工作区，与上一次commit保持一致 
$ git reset --hard
  
# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]
 
# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]
 
# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]
 
# 新建一个commit，用来撤销指定commit
# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]
 
# 暂时将未提交的
$ git stash
 
$ git stash pop
变化移除，稍后再移入
```

退出命令行git log 
按q就可以退出来到命令行了。

## push和pull命令
 1. Push ：直译过来就是「推」的意思，什么意思呢？如果你本地代码有更新了，那么就需要把本地代码推到远程仓库，这样本地仓库跟远程仓库就可以保持同步了。
- 代码示例：
- ``` git push origin master``` 
- 意思就是把本地代码推到远程 master 分支。

2. Pull：直译过来就是「拉」的意思，如果别人提交代码到远程仓库，这个时候你需要把远程仓库的最新代码拉下来，然后保证两端代码的同步。

- 代码示例：
- ```git pull origin master```
- 意思就是把远程最新的代码更新到本地。一般我们在 push 之前都会先 pull ，这样不容易冲突。

