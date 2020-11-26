---
title: Essays
date: 2020-10-15 19:17:56
categories: 
- Essays
tags:
- 
---

一个demo。
<!-- more -->

# demo (标题)

## 问题
xxx

## 原因和解决方法
xxx

## 参考链接
[xx](xxx)

# Anaconda使用conda activate激活环境出错

## 问题
使用激活python27环境时出错 
```shell
conda activate py27
CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.
```

## 原因和解决方法
```bash
# 激活环境
source activate
# 退出环境
conda deactivate
# 重新激活
conda activate py27
```

## 参考链接
[Anaconda使用conda activate激活环境出错](https://www.jianshu.com/p/cd0096b24b43)


# gitignore 不生效
## 问题
.gitignore 不生效的解决方案

## 原因和解决方法
当我们将 .gitignore 文件配置好后，却往往不能失效。git ignore只会对不在git仓库中的文件进行忽略，如果这些文件已经在git仓库中，则不会忽略。所以如果需要忽略的文件已经提交到本地仓库，则需要从本地仓库中删除掉（删除之前注意好备份！！！），如果已经提交到远端仓库，则需要从远端仓库中删除。并且要将 git 的本地缓存删除，然后重新提交。
```
git rm -r --cached . 
git add . 
git  commit -m "update .gitignore"
git push origin source
```

## 参考链接
### [gitignore 不生效的解决方案](https://blog.csdn.net/zwkkkk1/article/details/83550032)





