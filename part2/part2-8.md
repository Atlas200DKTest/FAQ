## 2.8 配置交叉编译环境时提示“Pack sysroot.tar.gz failed”
### 问题描述
配置交叉编译环境时提示“Pack sysroot.tar.gz failed”，如下图所示。
！[图2-3配置交叉编译环境失败](./img/2-3.png)


尝试直接使用命令ssh -p 22 HwHiAiUser@192.168.1.2，输入默认密码Mind@123，显示Permission Denied。
![图2-4登录失败](./img/2-4.png)


### 解决方法
1.从MindSpore Studio所在服务器SSH登录到开发者板失败，首先查看一下MindSpore Studio所在服务器的IP地址，如下图所示。
![图2-5MindSpore Studio所在服务器IP地址查看](./img/2-5.png)


由上图可看出USB虚拟网卡的IP地址与开发者板的IP地址不在同一网段。所以需要配置MindSpore Studio的USB网卡地址为与开发者板192.168.1.2在同一网段的IP地址。
2.使用路由器连接电脑和开发板，把路由器IP地址改成与开发者板在同一网段的IP地址（192.168.1.x）。
