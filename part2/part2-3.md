## 2.3 UI Host连接开发者板无法建立信任关系
### 问题描述
在UI Host所在Ubuntu服务器中，执行如下命令使用SSH方式连接Atlas 200 DK开发者板，提示无信任关系。
在UI Host中执行如下命令重新建立信任关系：
ssh-keygen -f "$HOME/.ssh/known_hosts" -R 192.168.1.2
其中192.168.1.2为Atlas 200 DK开发者板的IP地址。
报如下错误：
ECDSA host key for 192.168.1.2 has changed and you have requested strict checking.
### 解决方法
出现此错误是本地保存的SSH信息已失效导致，所以需要清空当前保存的SSH信息，然后重新建立连接。
#### 步骤1 
    清空UI Host中当前用户连接192.168.1.2主机的公钥信息。
ssh-keygen -R 192.168.1.2
#### 步骤2 
    重新以SSH方式连接Atlas 200 DK开发者板。
ssh HwHiAiUser@192.168.1.2
当提示如下信息时，输入yes重新建立SSH连接。
The authenticity of host '192.168.1.2' can't be established. 
ECDSA key fingerprint is 53:b9:f9:30:67:ec:34:88:e8:bc:2a:a4:6f:3e:97:95. 
Are you sure you want to continue connecting (yes/no)? 
----结束
