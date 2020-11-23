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