## 1.6 MindSpore Studio不支持开机自启动--删除
### 问题描述
服务器重启后，无法访问MindSpore Studio。
### 可能原因
MindSpore Studio不支持服务器重启自动拉起MindSpore Studio的相关服务。
### 解决方法
手工拉起服务操作如下，操作如下：
进入安装MindSpore Studio所在linux系统的/home/username/tools/bin目录下
![图1-8MindSpore Studio相关脚本所在目录](./img/1-8.jpg ''1-8'')


2.执行手动启动命令：bash start.sh
![图1-9执行手动启动命令](./img/1-9.jpg ''1-9'')


如上表示已经执行启动MindSpore Studio成功。
