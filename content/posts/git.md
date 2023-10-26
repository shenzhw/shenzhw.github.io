---
title: "Git Rebase命令详解"
date: 2023-10-20T14:52:30+08:00
draft: true
---

### 变基
我们假定代码仓主分支是develop分支。当做功能开发时，先从develop分支拉一个功能分支，如feat_user。

当我们在本地提交好代码准备推送到远程时，develop分支可能已经有人合入过最新的代码了。这时候我们要把develop分支的最新代码合并到feat_user分支，之所以这么做，有2个原因：

1. 把develop分支的代码合并到本地，做更好的集成测试，以免把feat_user分支合并到develop后产生问题。
2. 让提交历史更好看。

所谓变基，是指