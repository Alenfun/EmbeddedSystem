# Git  常用操作及技巧

[TOC]

## 一、Git 分支命令

- 创建name的分支，并切换过去
```sh
git checkout -b name
```
- 拉取远程分支，创建并切换到这个分支
```sh
git checkout -b name origin/remote-branch
git checkout -b 本地分支名 origin/远程分支名
```
- 查看所有分支
```sh
git branch -v
```
- 关联远程分支

```sh
git branch --set-upstream name origin/name
```
- 删除分支
```sh
git branch -d name
git branch -D name
```
- 合并到master
```sh
git checkout master
git merge name [-m "msg"]
```
- Git 推本地 master 到远端非 master 分支
```sh
git push origin master:fix_branch
```



## 二、Git 撤销本地提交

```
git reset --mixed HEAD~2
```

## 三、config配置

### 1. Git 查看config配置

```sh
git config --list
```

### 2. Git 设置用户名密码

```sh
git config --global user.name [username]
git config --global user.email [email]
```


### 3. Git 中设置代理

```sh
git config --global https.proxy http://127.0.0.1:1080
git config --global https.proxy https://127.0.0.1:1080

git config --global --unset http.proxy
git config --global --unset https.proxy
```



## 四、子模块仓库submodule

### 1.添加 submodule

为当前工程添加submodule，命令如下：

```
git submodule add repo_url path
```

其中，repo_url 是指子模块仓库地址，path 指将子模块放置在当前工程下的路径。 
注意：路径不能以 / 结尾（会造成修改不生效）、不能是现有工程已有的目录（不能顺利 Clone）。

命令执行完成，会在当前工程根路径下生成一个名为“.gitmodules”的文件，其中记录了子模块的信息。添加完成以后，再将子模块所在的文件夹添加到工程中即可。

强制添加可以使用  --force 参数。

### 2.更新 submodule

更新当前仓库中的 submodule，命令如下：

```sh
git submodule update --init --recursive
```

参数 `--recursive` 的意思是递归更新子模块，也就是会更新子模块的子模块，如果不加这个参数，则只会更新第一级的子模块。

### 3.删除 submodule

删除当前仓库中的 submodule，方法如下：

- 删除 .gitsubmodule  文件中对应的 submodule。

- 删除 .git/config 中对应的 submodule 项（这一步我测试的时候如果不做也可以，后面再次添加子模块的时候加上 --force 参数也可以再次添加）。

- 执行命令 `git rm --cached <submodule_path>`，执行命令前，请确保该 Git 仓库没有未提交的内容，否则会执行失败，示例如下：

```sh
git rm --cached hello
```

## 五、GIT与远程REPOSITORY同步TAG和BRANCH

参考如下地址：http://smilejay.com/2013/04/git-sync-tag-and-branch-with-remote/

## 六、 缓存区
- 暂存所有更改到本地分支
```sh
git stash
```
- 恢复
```sh
git stash pop
```

- 查看现有stash

```sh
git stash list
```

- 移除stash

```sh
git stash drop
```

```sh
$ git stash list
stash@{0}: WIP on master: 049d078 added the index file
stash@{1}: WIP on master: c264051 Revert "added file_size"
$ git stash drop stash@{0}
Dropped stash@{0} (364e91f3f268f0900bc3ee613f9f733e82aaed43)
```

- 查看指定stash的diff

```sh
git stash show 
```

