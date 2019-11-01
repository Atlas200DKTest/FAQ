## 6.2 USB连接方式时如何配置开发者板通过MindSpore Studio服务器连接网络
在MindSpore Studio所在服务器上配置路由规则，允许转发开发者板的IP报文。
开发者板上则需要配置一下路由地址，即MindSpore Studio所在服务器的IP地址。
MindSpore Studio所在服务器侧配置及开发者板侧的详细配置如下所示。
### MindSpore Studio所在服务器侧配置（UI Host侧配置）
 以root用户执行如下命令。
#### 1.执行如下命令允许报文转发。
echo "1" > /proc/sys/net/ipv4/ip_forward
#### 2.配置NAT转换。
sudo iptables -t nat -A POSTROUTING -o enp2s0 -s 192.168.1.0/24 -j MASQUERADE
其中enp2s0表示连接到外网的网卡， -s表示只对开发者板的IP报文做转换（192.168.1.0/24表示192.168.1.0-192.168.1.24之间的IP地址，开发者板的IP地址在此网段中即可）。
#### 3.配置转发规则。
sudo iptables -A FORWARD -i enp0s20f0u8 -o enp2s0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i enp0s20f0u8 -o enp2s0 -j ACCEPT
其中enp0s20f0u8为uihost上usb虚拟的网卡，表示数据报文的入口。
### 开发者板侧配置
#### 1.配置缺省路由。
sudo ip route change default via 192.168.1.251 dev usb0
此处192.168.1.251为MindSpore Studio所在服务器连接开发者板的网卡的ip地址，可通过ifconfig命令查看。

若执行此命令时提示TNELINK answers： No such file or directory，说明开发者板已经存在了此路由，只需要更改路由地址，例如修改此条命令为：
sudo ip route add default via 192.168.1.251 dev usb0
#### 2.在开发者板上添加DNS。
sudo vi /etc/resolvconf/resolv.conf.d/base
添加如下内容：
nameserver 114.114.114.114
执行:wq保存退出。
#### 3.执行如下命令使配置生效。
resolvconf -u
可执行cat /etc/resolv.conf命令确认文件内容。

