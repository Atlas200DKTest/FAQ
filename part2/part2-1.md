## 2.1 开发者板SD卡制卡失败
### 问题描述
SD卡制作失败，错误日志“make_ubuntu_sd.log”文件中有如下错误信息：
extrack package, file name:/root/tools/log/squashfs-root/opt/mini/mini_developerkit-XXXX.rar
extrack package(/root/tools/log/squashfs-root/opt/mini/mini_developerkit-XXX.rar) fail, installation failed

“make_ubuntu_sd.log”文件位于MindSpore Studio所在Ubuntu服务器中的“${toolpath}/bin”目录下。
“${toolpath}”为MindSpore Studio安装时配置，此路径可以通过“$HOME/Mind-Studio/scripts/env.conf”文件查看。
### 解决方法
产生此错误的原因为Ubuntu服务器中缺少unzip命令。
切换到root用户执行apt-get install unzip安装即可。
