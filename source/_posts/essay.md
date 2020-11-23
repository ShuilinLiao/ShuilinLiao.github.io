# 随记

## demo (标题)

### 问题

xxx

### 原因和解决方法

xxx

### 参考链接

[xx](xxx)



## Anaconda使用conda activate激活环境出错

### 问题

使用激活python27环境时出错 

```shell
conda activate py27
CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.
```

### 原因和解决方法

```bash
# 激活环境
source activate
# 退出环境
conda deactivate
# 重新激活
conda activate py27
```

### 参考链接

[Anaconda使用conda activate激活环境出错](https://www.jianshu.com/p/cd0096b24b43)



## gitignore 不生效

### 问题

.gitignore 不生效的解决方案

### 原因和解决方法

当我们将 .gitignore 文件配置好后，却往往不能失效。这是因为 .gitignore 只能忽略那些没有被追踪(`track`)的文件，因为 git 存在本地缓存，如果文件已经纳入了版本管理，那么修改 .gitignore 是不能失效的。那么解决方案就是要将 git 的本地缓存删除，然后重新提交。

```
git rm -r --cached . 
git add . git 
commit -m "update .gitignore"
```

### 参考链接

[.gitignore 不生效的解决方案](https://blog.csdn.net/zwkkkk1/article/details/83550032）

