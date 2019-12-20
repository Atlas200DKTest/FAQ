## 4.32 路由方式连接虚拟机，运行sample失败，报错 Failed to connect to server
### 问题描述
开发板插在交换机或路由器上，虚拟机通过网线连接路由器。在虚拟机中无法登录开发板，运行sample失败，报错日志如下
[ERROR] APP(2312,ascend_facedetectionapp):2019-01-01-00:35:43.606.308 [src/ascenddk/presenter/agent/net/socket_factory.cpp:99] Failed to connect to server: 192.168.0.19:7006 ,[src/ascenddk/presenter/agent/net/socket_factory.cpp:99:CreateSocket], Msg: the args not right
### 解决方法
需要把虚拟机桥接到连接路由器的那个网口，并且将这个网口的ip手动设置成和开发板同一网段的ip。然后在虚拟机中新增一个端口，如虚拟机的网口名是ens33，就加一个ens33:1，要设置和开发板ip同一网段的ip。设置之后。虚拟机无法上网，ping不通百度。但是可以连接开发板，直接部署就可以了。问题原因是depoly时，没有找到连接开发板的那个ip。但是按照如上步骤执行之后，depoly脚本可以自动识别192.168.0.223，这样运行就不会报错了步骤图如下：
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-32-1.jfif)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-32-2.jfif)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-32-3.jfif)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-32-4.jfif)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-32-5.jfif)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-32-6.jfif)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-32-7.jfif)
