## 1.10 联机帮助无法查看文档
### 问题描述
在Linux服务器安装MindSpore Studio后，单击界面“Help>Documents”，会弹出联机帮助界面，如图1.1所示，若单击目录后，内容无法刷新。
图1.1 联机帮助入口
### 解决方法
首先查看所使用的Linux服务器是否支持UTF-8字符集，如图1.1所示，命令为：locale，下面针对这两种情况分别给出解决措施。
图1.1 字符集查看


1. 若所使用的Linux服务器不支持UTF-8字符集。
安装UTF-8字符集，步骤如下：
a. 使用vi打开“/etc/default/locale”文件，将原来的内容修改为：
LANG="en_US.UTF-8" 
LANGUAGE="en_US.UTF-8:"
保存文件并退出，命令为：:wq!。
b. 执行如下命令：
locale-gen -en_US:en
若执行该命令后报错，可以忽略，直接往下执行。
c. 重启服务器，命令为：
reboot
若安装字符集重启服务器后，文档还是无法正常查看，则进入联机帮助文件所在目录，如“：~/tools/MindSpore-Studio-5.22.0/tomcat/webapps”，将该目录下面的docs文件删除后，重新解压“docs.war”包，命令为：unzip -d docs docs.war
2. 若所使用的Linux服务器已经支持UTF-8字符集。
在联机帮助文件所在目录，如“：~tools/MindSpore-Studio-5.22.0/tomcat/webapps”，执行如下命令：
convmv -f gb2312 -t UTF-8 --nosmart --notest -r docs
若文档还是无法正常查看，则将该目录下 docs文件删除后，重新解压“docs.war”包，命令为：unzip -d docs docs.war

