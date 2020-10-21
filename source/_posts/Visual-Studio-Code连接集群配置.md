---
title: Visual Studio Code连接集群配置
date: 2020-10-21 14:44:08
tags:
---

**第一步：安装插件**

配置远程开发首先需要安装一个名为**Remote - SSH**的插件，具体操作步骤如下，

- 点击扩展按钮
- 搜索**Remote - SSH**
- 安装

**第二步：配置VSCode**

step1: 点击VS code边栏的远程连接图标。![](/images/vscode/0.png)

step2: 点击SSH TARGETS右边的齿轮状⚙️按钮。

step3: 在弹出来的`C:\Users\XXX\.ssh\config`文件中添加下面内容，根据自己的用户名填写好各个字段，`Ctrl + s`保存。

```
# Read more about SSH config files: https://linux.die.net/man/5/ssh_config
Host gdl
	HostName 192.168.106.31
	User liaoshuilin
 	Port 22
```

step3: 设置terminal，Setting - Terminal - Integrated > Env:Windows - 点击 Edit in settings.json。（TERMINAL窗口中显示为1：powershell）

```
{
    "python.languageServer": "Microsoft",
    "terminal.integrated.shell.windows": "C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
    "workbench.iconTheme": "vscode-icons",
    "remote.SSH.remotePlatform": {
        "gdl": "linux"
    },
    "python.showStartPage": false,
    "explorer.confirmDelete": false,
    "window.zoomLevel": 1,
    "terminal.integrated.automationShell.windows": ""
}
```

**第三步：配置远程服务器**

这个需要windows配置有ssh工具，可以通过安装git、openssh实现。在本地打开cmd，

```
ssh-keygen
```

然后一直点击Enter键，不用输入任何内容，最后会在`C:\Users\user_name\.ssh`路径下生成公钥文件，可以看到有一个`id_rsa.pub`文件，然后通过FTP等方式把这个文件上传到远程服务器。进入集群SSH配置目录，`cd ~/.ssh`，查看一下是否有一个名为`authorized_keys`的文件，如果没有就创建一个，然后把刚上传的`id_rsa.pub`中的内容附到`authorized_keys`文件中，并更改文件权限

```
touch authorized_keys
cat ~/id_rsa.pub >> authorized_keys
chmod -R 600 authorized_keys
```

在本地的`C:\Users\user_name\.ssh\config`输入：

```
# Read more about SSH config files: https://linux.die.net/man/5/ssh_config
Host gdl
    HostName 192.168.106.31
    User liaoshuilin
    Port 22
```



### 参考链接

1. [**VS Code远程开发**](https://zhuanlan.zhihu.com/p/93239107)
2. [Windows10系统下使用VS code远程连接集群（在有跳板机的情况下）](https://blog.csdn.net/yamengxi/article/details/108156610)