## 5.12 命令行跑profiling 报 startHiAiDaemon error
### 问题描述
命令行方式跑 profiling 报 startHiAiDaemon error

![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-12-1.png)


### 问题分析
查看单板网络状态，连接状态异常，ifconfig查看 ens35u1没有IP，启动Daemon 失败
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-12-2.png)

### 问题处理
重新启动ens35u1状态，
ifdown  ens35u1
ifup  ens35u1
使单板端口有ip 192.168.1.134后，
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-12-3.png)
运行profiling不报该错误。
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-12-4.png)
