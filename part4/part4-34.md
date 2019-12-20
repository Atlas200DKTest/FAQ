## 4.34 socket连接失败：open channel failed
### 问题描述
单板上运行facedetection程序，程序运行后，present界面看不到摄像头，查看log日志，log 打印：Open channel failed ，server： 192.168.1.166：7006
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-34-1.png)
### 问题分析
和单板对接的主机ip实际是 192.168.1.134

![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-34-2.png)

单板，连接192.168.1.166可能连不上。channel的配置在graph.config文件中。

### 问题解决
修改graph.config中的presenterIP 为实际单板IP 192.168.1.134，修改后运行成功

