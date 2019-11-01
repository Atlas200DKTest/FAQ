## 1.1MindSpore Studio安装时执行apt-get update命令检查源配置出错
### 问题描述
#### 问题1：
MindSpore Studio部署前环境准备阶段，配置完源依赖后，执行apt-get update命令，报以下错误：
Aborted (core dumped)  
Reading package lists… Done  
E: Problem executing scripts APT::Update::Post-Invoke-Success ‘if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi’  
E: Sub-process returned an error code
#### 问题2：
MindSpore Studio部署前环境准备阶段，配置完源依赖后，执行apt-get update命令，报以下错误：
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)  
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
### 解决方法
#### 问题1解决方法：
缺少libappstream3库，执行如下命令进行先清除相关软件包，在执行更新：
sudo apt-get purge libappstream3 
sudo apt-get update
#### 问题2解决方法：
执行如下命令删除lock：
sudo rm /var/cache/apt/archives/lock 
sudo rm /var/lib/dpkg/lock
