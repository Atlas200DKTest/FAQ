## 2.24 运行profiling 报 not enough disk space
### 问题描述
运行profiling时报没有足够硬盘空间。
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-24-1.png)
登录单板使用 df 查看硬盘空间，显示如下：
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-24-2.png)
主机上使用df命令查看硬盘空间，显示如下：
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-24-3.png)
主机上/dev/sda1硬盘空间为100%，因此硬盘空间不够。
### 解决方法
删除主机上不用的文件，释放空间，重新运行profiling,可正常运行。

