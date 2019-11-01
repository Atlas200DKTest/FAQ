## 2.10 开发者板USB方式连接MindSpore Studio失败解决方法汇总
### 问题描述
参考《Ascend 310 Atlas 200 Developer Kit 使用指导》中的“配置Atlas 200 DK > 连接Atlas 200 DK与UI Host”进行连接后，仍然连接失败。
### 解决方法
#### 1. 环境检查。
​      如果Ubuntu系统是通过Windows主机上的VMWare或者VirtualBox进行部署的，请确保USB连接到虚拟机，而不是Windows。
​      如果是直接在主机上部署的Ubuntu操作系统或者USB已经连接到虚拟机，则执行以下检查。
 			请判断开发者板是否已上电，如果未上电，请上电。
 			若开发者板已上电，请执行ifconfig -a命令查看Ubuntu操作系统中的虚拟网卡是否已经启动，若未启动，请执行2。

#### 2. 虚拟网卡未启动。
若上电后虚拟网卡仍不可见，则怀疑USB 网口或数据线有问题，请尝试使用网线连接。
若网线连接成功，则结束，否则请转入3。
#### 3. 虚拟网卡已启动，但未绑定IP地址。
​	d. 查看/etc/network/interfaces文件，确认虚拟网卡IP是否已配置、配置是否正确，注意对比网卡名称、IP和ifconfig -a查看到的虚拟网卡名称、IP是否一致，以及IP是否配置正确，与192.168.1.2是否在一个网段。
​	e. 若interfaces文件中没有配置，请参考《Ascend 310 Atlas 200 Developer Kit 使用指导》中“配置Atlas 200 DK  > 连接Atlas 200 DK与UI Host” 中的USB连接场景下配置MindSpore Studio所在服务器的IP地址进行配置，并修改NetworkManager.conf文件中的”managed=false”为”managed=true”。
​	f. 若IP地址仍为生效，请切换到root用户并执行如下命令：
ifdown 网卡名
ifup 网卡名
service networking restart
service NetworkManager restart
​	g. 再使用ifconfig -a查看IP是否已生效，并且ping 192.168.1.2，若ping不通，请继续执行4

#### 4. 虚拟网卡与网卡静态IP均已启动，但无法ping通开发者板IP 192.168.1.2。
​	h. 若服务端Ubuntu所在的网段为192.168.1.x，可能会引起IP冲突，请参考：https://bbs.huaweicloud.com/forum/thread-16966-1-1.html。
​	i. 开发者板侧默认的usb0的静态IP可能被修改过，非192.168.1.2，请尝试其他常见网段，或者直接换网线连接上后查看usb0默认IP，或参考4.c。
​	j. 开发者板有问题导致开发板侧usb0的默认IP没有生效，此时若网线可以连接则使用网线连接，若网线连接不通，则使用串口线连接的方式查看ifconfig结果确认IP是否生效，请参考：https://bbs.huaweicloud.com/forum/thread-16962-1-1.html。如果没有生效，请查看串口启动日志，将日志导出发给华为工程师定位问题。

