## 2.5 在开发者板上无法ping域名，但可以ping通IP地址
### 问题描述
在开发板上无法ping 域名，但是可以ping + IP 地址。
### 解决方法
发生以上现象的原因为：自动获取DNS地址失败，导致无法进行DNS解析。
解决方法如下：
1.在Windows下查询局域网DNS服务器地址。
2.更改/etc/resolv.conf文件中的namesever 为1查询到的地址即可。
![](./img/2-5-1.png)
