## 1.11 如何升级Linux内核到4.18版本
### 问题描述
Mind Studio要求Linux的内核版本为4.18及以上版本，否则可能出现模型转换过程中，加载自定义算子插件时界面卡住的现象。
下面详细描述升级Linux内核版本的操作步骤。
### 解决方法
1. 执行uname -a命令查看Ubuntu的Linux内核版本是否低于4.18版本。
−如果高于4.18版本，则不需要升级内核。
−如果低于4.18版本，则按照如下步骤升级Linux的内核。
2. 下载Linux内核。
Linux内核的下载地址为https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D。
本示例下载v4.18-rc8版本的内核，需要下载如图1-13所示文件。
![图1-13](https://gitee.com/Atlas200DK/FAQ/raw/master/part1/img/1-13.jpg)

您可以在软件包上单击右键，选择“复制链接地址”，然后在Ubuntu后台使用root用户执行wget 链接地址命令下载相应的文件，例如：
a. 使用root用户创建一个文件夹用于存放内核文件。
例如：
su root
mkdir ~/kernel_v4.18
cd ~/kernel_v4.18
b. 执行如下命令下载所需的文件。
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18-rc8/linux-headers-4.18.0-041800rc8_4.18.0-041800rc8.201808052031_all.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18-rc8/linux-headers-4.18.0-041800rc8-generic_4.18.0-041800rc8.201808052031_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18-rc8/linux-image-unsigned-4.18.0-041800rc8-generic_4.18.0-041800rc8.201808052031_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18-rc8/linux-modules-4.18.0-041800rc8-generic_4.18.0-041800rc8.201808052031_amd64.deb
c. 在当前目录下使用dpkg命令安装下载的内核文件。
dkpg -i *.deb
如果执行此命令过程中缺少安装依赖，请执行apt-get install -f 命令自动安装缺少的依赖。
如果执行完上述命令后依旧出现缺失libssl1.1.0(>=1.1.0)的错误信息，请下载如下链接中的附件到Ubuntu服务器任一目录。
https://bbs.huaweicloud.com/forum/thread-22441-1-1.html
解压获取libssl1.1_1.1.0g-2ubuntu4.1_amd64.deb软件包，然后使用root用户执行如下命令手工安装libssll.1.1.0。
dkpg libssl1.1_1.1.0g-2ubuntu4.1_amd64.deb
然后再到~/kernel_v4.18 目录下进行内核的安装。
d.内核安装完后，请执行reboot命令重启系统。
重启完成后，执行uname -a查看内核版本号是否升级为4.18。

