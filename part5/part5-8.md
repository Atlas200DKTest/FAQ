## 508 重启linux 的网络服务，重起不了
### 问题描述
修改完/etc/network/interfaces文件后，在root用户下使用service networking restart失败

![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-8-1.png)


### 解决方法
可以尝试切换到普通用户下去执行命令：sudo service NetworkManager restart。之后网络服务重启，配置文件生效。

