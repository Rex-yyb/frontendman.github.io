# Git

## Git

### 基础概念

> Git 是一个开源的分布式版本控制系统,用于敏捷高效地处理任何或小或大的项目

+ 集中化的版本控制系统
> 有一个单一的集中管理的服务器，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新

+ 分布式版本控制系统
> 客户端并不只提取最新版本的文件快照，而是把代码仓库完整地镜像下来。 这么一来，任何一处协同工作用的服务器发生故障，事后都可以用任何一个镜像出来的本地仓库恢复

#### 三个分区

- 工作区（working directory）
- 暂存区（stage）
- 版本库

![section](https://note.youdao.com/yws/api/personal/file/WEB68995963b351ce17e60945ce08c4cc62?method=download&shareKey=b6ce41f815d6c73afff5c2ec76490460)

### git配置

#### git config

三个不同的作用域
```
git config --system
git config --global
git config --local
```

#### user.name与user.email

``user.name``和``user.email``指的是用户名和邮箱，这些两个配置会被添加到提交信息中

1. 添加配置

``git config --local user.name "xiao" git config --local user.email xiao@git.com ``

2. 删除配置

``git config --unset <参数名>``

#### .gitignore

.gitignore文件配置不被git跟踪的文件


### git 常用命令

- git init (创建新的 Git 仓库)
- git clone (拷贝git仓库)
- git add (工作区 => 暂存区)
- git commit (暂存区 => 版本库)
- git rm (删除版本库中的文件)
```
git rm 命令的本质就是 rm 和 git add
git rm --cached 工作区保留文件
```
- git pull (拉取远程代码)
- git push (推送代码到远程)
- git help (获取帮助)
- git log (查看提交历史)
- git reflog (可以查看所有分支的所有操作记录)
- git diff (比较文件在暂存区和工作区的差异)

### 分支操作

+ git branch (查看当前版本库分支)
+ git branch -a (查看所有分支，包括本地分支和本地远程分支)
+ git branch new_branch (创建分支)
+ git branch -b new_branch (创建并切换)
+ git checkout [branch]  (切换分支)
+ git branch -d new_branch (删除本地分支)
+ git push origin --delete [branch_name] (删除远程分支)
+ git merge  (合并分支)

### 撤销回退

#### git checkout

放弃工作区的修改
```
// 放弃单个文件修改,注意不要忘记中间的"--",不写就成了检出分支了!
git checkout -- filepathname
// 放弃所有的文件修改
git checkout .  
```

#### git reset

> git-reset - Reset current HEAD to the specified state

![image](https://note.youdao.com/yws/api/personal/file/WEB5aa010881ec475aefc10c74338b98825?method=download&shareKey=eef426c4e957106e2131ba82e95d73c4)

- --mixed：为默认值，等同于git reset。作用为：将文件回退到工作区，此时会保留工作区中的文件，但会丢弃暂存区中的文件；
- --soft：作用为：将文件回退到暂存区，此时会保留工作区和暂存区中的文件；
- --hard：作用为：将文件回退到修改前，此时会丢弃工作区和暂存区中的文件；

#### git revert

回滚某个commit
```
git revert HEAD 撤销前一次 commit
git revert HEAD^ 撤销前前一次 commit
git revert commit 
```

### git stash

stash命令可用于临时保存和回复修改,可跨分支

- git stash
```
git stash -u 未跟踪的文件也会保存
```
- git stash pop
- git stash apply
- git stash apply stash@{n}
- git stash list

## github 审核机制

通过 PR 方式提交内容，审核者在 PR 下 ``Files changed`` 视图中右侧针对某行进行 comment

![](https://note.youdao.com/yws/api/personal/file/WEB0c74ebe6624cf13173a5dc236b8769cb?method=download&shareKey=3d9f7fb22d9339c48e91a186428dbb23)

参考掘金翻译计划[参与翻译](https://github.com/xitu/gold-miner/wiki/%E5%A6%82%E4%BD%95%E5%8F%82%E4%B8%8E%E7%BF%BB%E8%AF%91)

### 参考文章

- [Git详解1-Git分区，配置与日志](https://juejin.cn/post/6933863550683185160)