## 2.19 无法连接开发板[port 22: No route to host]
### 问题描述
无法连接开发板[port 22: No route to host]
我想修改开发板用nic网卡连接的网段，连入开发板之后，vim /etc/network/interfaces，
把auto eth0中的address改成了192.168.1.3，和usb在同一个网段，保存之后重启就无法再连接了
用usb连接会出现No route to host
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-19-1.png)
虚拟机的配置：
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-19-2.png)
### 解决方法
虚拟机通过网线连开发板情况比较复杂，首先虚拟机得桥接到你对应的物理网卡，然后设置物理网卡IP和你的开发板在同一网段。
在用户的操作里，修改开发板网口IP为192.168.1网段是没法通过网线连接开发板的。USB也连不上，应该是因为修改interfaces文件有误导致USB口也连不上。
要解决连不上的问题，可以：
a) 给开发板下电，拔出SD卡。用读卡器读取SD卡，可以看到有三个分区。找到存在/etc/network/interfaces文件的分区，在root用户下打开interfaces文件，复原interfaces文件即可
b) 或者可以重新制卡解决问题

