## 1.6 MindStudio不支持开机自启动--删除
### 问题描述
服务器重启后，无法访问MindStudio。
### 可能原因
MindStudio不支持服务器重启自动拉起MindStudio的相关服务。
### 解决方法
手工拉起服务操作如下，操作如下：
进入安装MindStudio所在linux系统的/home/username/tools/bin目录下

![图1-8](https://gitee.com/Atlas200DK/FAQ/raw/master/part1/img/1-8.jpg)


2. 执行手动启动命令：bash start.sh

![图1-9](https://gitee.com/Atlas200DK/FAQ/raw/master/part1/img/1-9.jpg)


如上表示已经执行启动MindStudio成功。
