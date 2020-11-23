

## 什么是Anaconda

Anaconda 是一个流行的 Python/R 数据科学和机器学习平台，大数据处理，预测分析，和科学计算。

Anaconda 发行版附带了250个开源数据软件包，并且超过 7500 个软件包可以从 Anaconda 软件源中安装。它同时还包含了一个命令行工具和一个被称为"Anaconda Navigator"的图形用户界面。

这个指南将会跟你解释在 Ubuntu 20.04 上的 Anaconda Python 发行版安装过程。

## 安装Anaconda

在写这篇文章的时候，Anaconda 最新绑定版本是 2020.02。在下载安装脚本之前，浏览[下载页面](https://www.anaconda.com/products/individual)，并且检查是否有更新的Anaconda 可用。

- 在 Ubuntu 20.04 上完成下面的步骤，安装 Anaconda。使用你的浏览器或者`wget`去下载 Anaconda 安装脚本：

```shell
wget -P /tmp https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh
```

- 这一步可选的，但是我们推荐你去验证脚本的数据完整性。

```shell
sha256sum /tmp/Anaconda3-2020.02-Linux-x86_64.sh
```

输出类似于：

```shell
2b9f088b2022edb474915d9f69a803d6449d5fdb4c303041f60ac4aefcc208bb  /tmp/Anaconda3-2020.02-Linux-x86_64.sh
```

确保上面的命令打印出来的哈希值和[Anaconda with Python 3 on 64-bit Linux page](https://docs.anaconda.com/anaconda/install/hashes/lin-3-64/)页面对应版本的 Anaconda 哈希值一样。

```shell
https://docs.anaconda.com/anaconda/install/hashes/Anaconda3-2020.02-Linux-x86_64.sh-hash/
```

- 运行脚本启动安装进程：

```shell
bash /tmp/Anaconda3-2020.02-Linux-x86_64.sh
```

看到以下输出：

```shell
Welcome to Anaconda3 2020.02
In order to continue the installation process, please review the license
agreement.
Please, press ENTER to continue
>>>
```

- 按`ENTER`继续。往下滑动阅读协议，使用`ENTER`按键。一旦你看完协议，你将会被询问是否接受协议条款：

```shell
Do you approve the license terms? [yes|no]
```

输入`yes`接受协议，并且你会被提示选择安装路径：

```shell
Anaconda3 will now be installed into this location:
/home/linuxize/anaconda3

    - Press ENTER to confirm the location
    - Press CTRL-C to abort the installation
    - Or specify a different location below
```

安装过程将会花费一些时间，并且一旦完成，脚本将会问你是否想要运行`conda init`。输入`yes`。

```shell
Installation finished.
Do you wish the installer to initialize Anaconda3
by running conda init? [yes|no]
```

这将会将命令行工具`conda`添加到系统的`PATH`环境变量中。

- 想要激活 Anaconda，你可以关闭并且重新打开你的 shell 或者在当前 shell 会话中输入下面的命令，来重新加载`PATH`环境变量：

```shell
source ~/.bashrc
```

想要验证安装过程，在你的终端输入`conda`。

就这些。你已经成功地在你的 Ubuntu 机器上安装好了 Anaconda， 你可以开始使用它了。

## 更新Anaconda

打开你的终端，并且输入：

```shell
conda update --all
```

如果有更新，`conda`将会显示一个列表，并且提示你确认是否更新：

```shell
The following packages will be UPDATED:

  anaconda-navigator                          1.9.12-py37_0 --> 1.9.12-py37_1
  conda                                        4.8.2-py37_0 --> 4.8.3-py37_0
  conda-package-han~                   1.6.0-py37h7b6447c_0 --> 1.6.1-py37h7b6447c_0


Proceed ([y]/n)? 
```

## 卸载 Anaconda

如果你想从你的 Ubuntu 系统中卸载 Anaconda，移除 Anaconda 安装目录以及其他在安装过程中创建的文件：

```shell
rm -rf ~/anaconda3 ~/.condarc ~/.conda ~/.continuum
```

打开`~/.bashrc`，并且从环境变量中移除 Anaconda

## Windows系统安装Anaconda

1. 前往[官方下载页面](https://docs.anaconda.com/anaconda/install/windows/)下载。有两个版本可供选择：Python 3.6 和 Python 2.7，选择版之后根据自己操作系统的情况点击“64-Bit Graphical Installer”或“32-Bit Graphical Installer”进行下载。

2. 完成下载之后，双击下载文件，启动安装程序。

   ① 如果在安装过程中遇到任何问题，那么暂时地关闭杀毒软件，并在安装程序完成之后再打开。

   ② 如果在安装时选择了“为所有用户安装”，则卸载Anaconda然后重新安装，只为“我这个用户”安装。

3. 选择“Next”。

4. 阅读许可证协议条款，然后勾选“I Agree”并进行下一步。

5. 除非是以管理员身份为所有用户安装，否则仅勾选“Just Me”并点击“Next”。

6. 在“Choose Install Location”界面中选择安装Anaconda的目标路径，然后点击“Next”。

   ① 目标路径中不能含有空格，同时不能是“unicode”编码。

   ② 除非被要求以管理员权限安装，否则不要以管理员身份安装。

7. 在“Advanced Installation Options”中不要勾选“Add Anaconda to my PATH environment variable.”（“添加Anaconda至我的环境变量。”）。因为如果勾选，则将会影响其他程序的使用。如果使用Anaconda，则通过打开Anaconda Navigator或者在开始菜单中的“Anaconda Prompt”（类似macOS中的“终端”）中进行使用。

   除非你打算使用多个版本的Anaconda或者多个版本的Python，否则便勾选“Register Anaconda as my default Python 3.6”。

   然后点击“Install”开始安装。如果想要查看安装细节，则可以点击“Show Details”。

8. 点击“Next”。

9. 进入“Thanks for installing Anaconda!”界面则意味着安装成功，点击“Finish”完成安装。

   如果你不想了解“Anaconda云”和“Anaconda支持”，则可以不勾选“Learn more about Anaconda Cloud”和“Learn more about Anaconda Support”。

10. 验证安装结果。可选以下任意方法：

    ① “开始 → Anaconda3（64-bit）→ Anaconda Navigator”，若可以成功启动Anaconda Navigator则说明安装成功。

    ② “开始 → Anaconda3（64-bit）→ 右键点击Anaconda Prompt → 以管理员身份运行”，在Anaconda Prompt中输入 conda list ，可以查看已经安装的包名和版本号。若结果可以正常显示，则说明安装成功。

    

## 参考链接

[如何在 Ubuntu 20.04 上安装 Anaconda](https://cloud.tencent.com/developer/article/1649008)

[Anaconda介绍、安装及使用教程](https://zhuanlan.zhihu.com/p/32925500)