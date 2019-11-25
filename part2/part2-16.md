## 2.16 如何配置开发者板通过网口直接连接网络
### 问题描述 
Atlas 200 DK开发者板如何不适用配置路由转发的方式，直接通过网口连接网络？
### 问题描述
1. 登录开发者板，并切换到root用户，打开interfaces文件。
vim /etc/network/interfaces
2.  将eth0配置为DHCP方式获取IP地址。
auto eth0 
iface eth0 inet dhc
保存退出interfaces文件。
3. 重启开发者板，通过USB端口连接开发者板，执行ifconfig命令即可看到开发者板已经分配了IP地址。
HwHiAiUser@davinci-mini:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 9a:28:91:80:fa:2f
          inet addr:192.168.221.224  Bcast:192.168.221.255  Mask:255.255.254.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:2266 (2.2 KB)  TX bytes:2193 (2.1 KB) 
          Interrupt:69  
 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0  
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB) 
 
usb0      Link encap:Ethernet  HWaddr fe:ef:37:29:76:7d
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:355 errors:0 dropped:45 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000  
          RX bytes:36914 (36.9 KB)  TX bytes:30407 (30.4 KB)
4. 测试网络连通性。
执行ping www.baidu.com命令也可以ping通，如下所示：
HwHiAiUser@davinci-mini:~$ ping www.baidu.com 
PING www.a.shifen.com (112.80.248.76) 56(84) bytes of data. 
64 bytes from 112.80.248.76: icmp_seq=1 ttl=57 time=2.11 ms 
64 bytes from 112.80.248.76: icmp_seq=2 ttl=57 time=2.31 ms 
64 bytes from 112.80.248.76: icmp_seq=3 ttl=57 time=1.79 ms 
64 bytes from 112.80.248.76: icmp_seq=4 ttl=57 time=2.37 ms 
^C 
--- www.a.shifen.com ping statistics --- 
4 packets transmitted, 4 received, 0% packet loss, time 3005ms 
rtt min/avg/max/mdev = 1.795/2.147/2.370/0.229 ms
执行apt-get命令，也可以使用，如下所示：
root@davinci-mini:/home/HwHiAiUser# apt-get update 
Get:1 http://ports.ubuntu.com/ubuntu-ports xenial InRelease [247 kB] 
Get:2 http://ports.ubuntu.com/ubuntu-ports xenial-security InRelease [109 kB] 
Get:3 http://ports.ubuntu.com/ubuntu-ports xenial-updates InRelease [109 kB] 
Get:4 http://ports.ubuntu.com/ubuntu-ports xenial/main arm64 Packages [1,130 kB] 
Get:5 http://ports.ubuntu.com/ubuntu-ports xenial/main Translation-en [568 kB] 
Get:6 http://ports.ubuntu.com/ubuntu-ports xenial-security/main arm64 Packages [480 kB] 
Get:7 http://ports.ubuntu.com/ubuntu-ports xenial-security/main Translation-en [291 kB] 
Get:8 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main arm64 Packages [728 kB] 
Get:9 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main Translation-en [402 kB] 
Fetched 4,064 kB in 4s (865 kB/s)
Reading package lists... Done
