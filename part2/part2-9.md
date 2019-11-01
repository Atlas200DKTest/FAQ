## 2.9 实验室Ubuntu机器使用192.168.1.xx网段，开发者板连接IP冲突
### 问题描述
目前很多局域网内的PC或者服务器都是配置的192.168.1.xxx网段IP，而且IP都是自动分配的，所以如果采用USB方式连接时开发者板，则开发者板的IP默认是192.168.1.xxx网段，PC端USB虚拟网卡的IP也需要是192.168.1.xxx网段IP，则很容易出现IP冲突。
### 解决方法
1. 先将MindSpore Studio所在的Ubuntu机器网线拔掉（避免IP冲突），然后通过USB方式连接开发者板，用HwHiAiUser登录开发者板（192.168.1.2）。
2. 在开发者板上切换到root用户，然后修改usb0的网卡静态IP为其他网段，例如192.168.2.xxx，编辑/etc/network/interface, 作如下修改：
auto usb0 
iface usb0 inet static 
address 192.168.2.2 
netmask 255.255.255.0
此处配置开发者板的IP地址为192.168.2.2。
3. 下电开发者板，然后重新上电开发者板，开发者板usb0网卡的IP将会生效，这时候再配置ubuntu下的usb虚拟网卡IP为192.168.2.xxx，例如192.168.2.134。
4. 插上Ubuntu机器的网线，IP冲突就会解决了。

