## 1 配置window terminal

建议使用window terminal登陆集群，可通过Microsoft store下载**window terminal**以及**Ubuntu 20**，提供登陆界面，借用后者的ssh等命令，直接使用ssh登陆集群。  

- 进入电脑安全模式开启cpu开关（个别电脑需要）；

- 开启window的WSL功能：前往 “启用或关闭 Windows 功能” ，然后滚动至底部，如截图所示，勾选 “适用于 Linux 的 Windows 子系统”，点击确定。它将会下载安装需要的包。安装完成之后，系统将会询问是否重启。重启设备。

- 进入Microsoft store下载Ubuntu 20和window terminal；

- 下载window terminal后，启动并选择Ubuntu。配置window terminal界面，参考[配置文件](documents/ubuntu_settings.json)。

- 此时Linux虚拟系统已经初步建立，进入d盘：`cd /mnt/d`

- 在运行(`win+R`)或`cmd`里直接输入`\\wsl$`进入Ubuntu的目录，从而查看ubuntu在windows上home的目录 `\\wsl$\Ubuntu-20.04\home`

  以个人系统为例，WSL的root目录对应windows的：`C:\Users\liaos\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu20.04onWindows_79rhkp1fndgsc\LocalState\rootfs`   其中AppData文件夹默认是隐藏的

  

## 2 免密码登录服务器以及与服务器传输文件

```shell
# 本地进入home目录，并生成rsa密码
cd 
ssh-keygen -t rsa
# 登录服务器
ssh liaoshuilin@192.168.106.31
# 将公钥复制粘贴到大型机的.ssh目录下authorized_keys（若没有，则创建）
cat ~/.ssh/id_rsa.pub
vi ~/.ssh/authorized_keys  
```



## 3 本地与集群传输文件

使用[scp](https://www.cnblogs.com/likui360/p/6011769.html)命令，在使用期先设置集群的别名信息，方便使用scp命令

```shell
echo -e "Host  alias1 \n HostName 192.114.23.43 \n User username" > ~/.ssh/config 
```

alias1为设置的别名，username为在集群上的用户名，最后呈现格式为

```shell
Host  gdl
HostName 192.114.23.43
User xxx
```

传输文件一般在本地进行command

```shell
scp -r alias1:/hwfssz1/filedir/  ./  # 集群传输到本地
scp file.txt  alias2:/hwfssz1/filedir/  # 本地传输到集群
```



## 4 参考链接

[Cygwin：Linux模拟软件](https://zouhua.top/archives/16954f4d.html)

[windows10 ubuntu子系统 WSL文件位置](https://www.cnblogs.com/lepeCoder/p/wsl_dir.html)