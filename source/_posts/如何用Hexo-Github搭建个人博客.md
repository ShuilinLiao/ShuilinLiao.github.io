---
title: 如何用Hexo+Github搭建个人博客
date: 2020-10-15 19:17:56
tags:
---

## Git与GiHub的配置

****

**<u>这一步主要目的为执行Git的安装，并将GitHub远程仓库克隆到本地，以方便后续更新的博客内容同步到GitHub远程仓库</u>**

### **GitHub创建个人仓库**

登录到GitHub,如果没有GitHub帐号，使用你的邮箱注册GitHub帐号：[Build software better, together](https://link.zhihu.com/?target=https%3A//github.com/) 点击GitHub中的New repository创建新仓库，仓库名应该为：`用户名.github.io` 这个**用户名**使用你的GitHub帐号名称代替。

### **安装GitHub**

什么是Git ?简单来说Git是开源的分布式版本控制系统，用于敏捷高效地处理项目。我们网站在本地搭建好了，需要使用Git同步到GitHub上。如果想要了解Git的细节，参看[廖雪峰](https://link.zhihu.com/?target=http%3A//weibo.com/liaoxuefeng)老师的Git教程：[Git教程](https://link.zhihu.com/?target=http%3A//www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000) 。安装成功后，将你的Git与GitHub帐号绑定，鼠标右击打开Git Bash

创建名为“Blog”的目录，以下命令可以在git bash界面处理

设置user.name和user.email配置信息：

```
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub注册邮箱"
```

生成ssh密钥文件：

```
ssh-keygen -t rsa -C "你的GitHub注册邮箱"
```

然后直接三个回车即可，默认不需要设置密码
然后找到生成的.ssh的文件夹中的id_rsa.pub密钥，将内容全部复制

打开[GitHub_Settings_keys](https://link.zhihu.com/?target=https%3A//github.com/settings/keys) 页面，新建new SSH Key

Title为标题，任意填即可，将刚刚复制的id_rsa.pub内容粘贴进去，最后点击Add SSH key。
在Git Bash中检测GitHub公钥设置是否成功，输入 ssh git@github.com ：

如上则说明成功。这里之所以设置GitHub密钥原因是，通过非对称加密的公钥与私钥来完成加密，公钥放置在GitHub上，私钥放置在自己的电脑里。GitHub要求每次推送代码都是合法用户，所以每次推送都需要输入账号密码验证推送用户是否是合法用户，为了省去每次输入密码的步骤，采用了ssh，当你推送的时候，git就会匹配你的私钥跟GitHub上面的公钥是否是配对的，若是匹配就认为你是合法用户，则允许推送。这样可以保证每次的推送都是正确合法的。

```
git clone git@github.com:theme-next/theme-next.org.git
```

主题文件（在Blog目录下执行）：

克隆博客仓库

```
git clone git@github.com:ShuilinLiao/ShuilinLiao.github.io.git
git branch # 显示当前在main分支
git checkout -b source # 创建并切换到source分支 因调整source为默认主支，因此克隆后直接是源代码仓库
```

## hexo搭建博客
### **安装Node.js**

Hexo基于Node.js，Node.js下载地址：[Download | Node.js](https://link.zhihu.com/?target=https%3A//nodejs.org/en/download/) 下载安装包，注意安装Node.js会包含环境变量及npm的安装，安装后，检测Node.js是否安装成功，在命令行中输入 `node -v` 。检测npm是否安装成功，在命令行中输入`npm -v` 。

### **安装Hexo**

Hexo就是我们的个人博客网站的框架， 这里需要自己在电脑常里创建一个文件夹，可以命名为Blog，Hexo框架与以后你自己发布的网页都在这个文件夹中。

- 从Git bash里面进入我们Blog目录，使用npm命令安装Hexo，输入：

```bash
npm install -g hexo-cli 
```

如果碰到卡住问题，可以通过在安装前执行以下命令，改变镜像使安装加快

`npm config set registry https://registry.npm.taobao.org`

- 安装完成后，初始化我们的博客（在Blog目录下），输入：

```bash
hexo init "xx's blog"
```

- 复制/剪切 xx's blog **`内容`**至博客仓库 username.github.io

- 更换主题：如果你不喜欢Hexo默认的主题，可以更换不同的主题，主题传送门：[Themes](https://link.zhihu.com/?target=https%3A//hexo.io/themes/)。 如：我自己使用的是Next主题，可以在blog目录中的themes文件夹中查看你自己主题是什么。现在把默认主题更改成Next主题，在blog目录中（就是命令行的位置处于blog目录），打开命令行输入以下，将Next主题下载到blog目录的themes主题下的next文件夹中：

  ```
  git clone https://github.com/iissnan/hexo-theme-next themes/next
  ```

- 删除theme里的hexo-theme-next（而不是github.io内的.git）内置的.git目录和.github目录，防止同步到Github远程仓库的时候出现冲突；

- 打开**站点**的_config.yml配置文件，修改主题为next；

- 打开**主题**的_config.yml配置文件，不是站点主题文件，找到Scheme Settings。next主题有三个样式，选择你自己喜欢的样式（只需要把行首的#去除，#是注释），选择好后，再次部署网站，hexo g、hexo d，查看效果。

### 本地预览

- 为了检测我们的网站雏形，分别按顺序输入以下三条命令：

```
hexo new my_test # 新建文章
hexo g # 生成
hexo s # 部署
```

- 完成后，打开浏览器输入地址：

```
http://localhost:40000
```

- 安装**Typora**软件，为了编辑md文件。

### 发布网站

上面只是在本地预览，接下来要做的就是就是推送网站，也就是发布网站，让我们的网站可以被更多的人访问。在设置之前，需要解释一个概念，在ShuilinLiao.github.io根目录（即之前初始化的Shuilin's blog的根目录）里的_config.yml文件称为**站点**配置文件。

关联Hexo与GitHub，修改根目录下面（我的为ShuilinLiao.github.io）的站点配置文件_config.yml，并保存。

```
deploy:
    type: git
    repo: https://github.com/ShuilinLiao/username.github.io.git
    branch: master
```

其实就是给hexo d 这个命令做相应的配置，让hexo知道你要把blog部署在哪个位置，很显然，我们部署在我们GitHub的仓库里。最后安装Git部署插件，输入命令：

```basemake
npm install hexo-deployer-git --save
```

这时，我们分别输入三条命令：

```bash
hexo clean 
hexo g 
hexo d
```

其实第三条的 hexo d 就是部署网站命令，d是deploy的缩写。完成后，打开浏览器，在地址栏输入你的放置个人网站的仓库路径，即 [http://xxxx.github.io](https://link.zhihu.com/?target=http%3A//xxxx.github.io) 

你就会发现你的博客已经上线了，可以在网络上被访问了。

我们开始正式发布上线博客文章，在命令行中输入：

```
hexo n "博客文章名字"
```

我们会发现在blog根目录下的source文件夹中的_post文件夹中多了一个 **博客文章名字.md** 文件，使用**Typora**软件打开编辑，就可以开始你的个人博客之旅了。

编辑好之后生成和部署。`hexo g` 和 `hexo d`

在hexo d推送网站后，可以将源代码上传至GitHub的博客仓库source分支。

git bash处跳转到当前博客目录，根目录下输入博客所在目录

```
cd username.github.io
```

一定是在source分支查看文件是否存在修改

```
git status
```

提交修改文件至远程仓库

```
git add 博客文章名字.md # git add -A
git commit -m "update files"
git push origin source
# git push origin
```

随后可以在浏览器中输入域名浏览。



### 参考链接

1. [Hexo搭建个人博客](https://zouhua.top/archives/ec7d7221.html#more)
2. [GitHub+Hexo 搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)