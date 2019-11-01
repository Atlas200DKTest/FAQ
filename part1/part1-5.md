## 1.5 MindSpore Studio或DDK安装过程中提示pip2或pip不可用
### 问题描述
MindSpore Studio或DDK安装过程中提示pip2或pip不可用，并退出安装，提示信息如图1-6、图1-7所示。
![图1-6 pip2不可用提示信息]
(./img/1-6.jpg ''1-6'')

![图1-7 pip不可用提示信息]
(./img/1-7.jpg ''1-7'')

### 可能原因
该问题可能是由于pip重新安装过程中，pip2没有正确更新。
### 解决方法1
步骤 1 su root切换到root用户，执行pip list，如果返回信息没有错误提示，说明pip可用；执行pip2 list提示错误，说明pip2不可用。
步骤 2 root用户下删除pip2，删除命令为：rm /usr/bin/pip2。
步骤 3 将pip2软连接到pip，命令为：ln -s pip pip2。
步骤 4 再次执行pip2 list，若返回信息没有错误提示，则说明问题解决。
若pip、pip2仍不可用，则参见解决方法2。
### 解决方法2
如果依赖安装过程中pip安装异常，请依次执行如下命令。
sudo apt-get remove python-pip python3-pip 
wget https://bootstrap.pypa.io/get-pip.py 
python get-pip.py --user 
python3 get-pip.py  --user
