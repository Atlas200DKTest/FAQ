## 4.12 textfile busy
### 问题描述
应用程序执行时，报如下错误：
textfile busy错误示例
![4-12-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-12-1.jpg)
### 解决方法
出现textfile busy的原因为文件被其他进程占用。
步骤 1执行fuser命令查看当前使用该文件的进程ID。
[root@localhost]# fuser <程序文件名> 
<程序文件名>:         50340
步骤 2停止使用该文件的进程。
[root@localhost]# kill -9 50340
