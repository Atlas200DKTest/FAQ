## 2.12 开发者板USB方式连接UI Host，通过UI Host连网相关案例
### 问题描述
参考6.2USB连接方式时如何配置开发者板通过MindSpore Studio服务器连接网络将开发者板通过UI Host进行连网。
在UI Host上配置的信息，系统重启后，就失效了，需要重新配置。
在开发板上配置的缺省路由sudo ip route change default via 192.168.1.251 dev usb0，每次开发者板重启，也会失效，需要重新配置。
### 解决方法
#### MindSpore Studio所在服务器侧配置（UI Host侧配置）重启失效问题
	对于第一步echo "1" > /proc/sys/net/ipv4/ip_forward，ip_forward文件中配置的值失效问题。
解决方法：
	将“/etc/sysctl.conf”文件中的这一行net.ipv4.ip_forward=1，取消注释；然后执行sysctl -p，则 “/proc/sys/net/ipv4/ip_forward”文件中的值重启就不会失效了。
对于2与3步骤中UI Host中的NAT转换与转发规则的iptables的配置失效的问题。
 	解决方法：
执行如下命令安装iptables-persistent
sudo apt-get install iptables-persistent
然后参考2与3重新配置NAT转换与转发规则。
配置完后，执行如下命令将配置的规则存储在“/etc/iptables/rules.v4”与“/etc/iptables/rules.v6”文件中。
sudo netfilter-persistent save
则系统每次重启时，会自动执行sudo netfilter-persistent reload命令来启用所存储的iptables规则，iptables规则可以通过sudo iptables -nvL --line-number命令查看。
#### 开发者板侧缺省路由配置重启失效问题
在文件“/etc/rc.local”中的exit 0前，加上sudo ip route change default via 192.168.1.251 dev usb0即可。
此处192.168.1.251为MindSpore Studio所在服务器连接开发者板的网卡的ip地址，可通过ifconfig命令查看，参考1。
