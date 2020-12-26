---
title: git基本命令
date: 2020-12-26 17:47:18
categories: 开发
tags: git
---

## Git 全局设置:
``` bash
git config --global user.name "hujianwen"
git config --global user.email "hjwfree@163.com"
```

## 创建 git 仓库:
``` bash
mkdir gkmobile
cd gkmobile
git init
touch README.md
git add .
git commit -m "first commit"
git remote add origin https://gitee.com/...
git push -u origin master
```

## 已有仓库?
``` bash
cd existing_git_repo
git remote add origin https://gitee.com/...
git push -u origin master
```

## 可能会遇到的一些问题
### git submodule 情况处理
当你的项目里面包含两个或两个以上的仓库地址时，提交代码会失败,比如我这个hexo项目，引入了别人的仓库代码，报错如下：
``` bash
Your branch is up to date with 'origin/hexo'.

Changes not staged for commit:
        modified:   themes/butterfly (modified content)

no changes added to commit
```
这个时候你只要删除掉themes/butterfly子模块
删除之后再添加进去就行了，后续提交成功

``` bash
git rm --cached themes/butterfly
git add themes/butterfly/
git commit -m '备份主题'
```

### 本地切换远程仓库地址
有时候我们的本地项目需要切换远程项目地址
先删除本地的所有远程仓库连接，再添加你想要连接的新地址
```bash
git remote rm origin
git remote add origin git.com...
```

### 修改远程github的默认分支
打开github的setting设置模块，里面可以修改默认分支
默认分支主要是影响到git clone 所拉取的内容