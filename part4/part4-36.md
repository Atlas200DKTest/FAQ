## 4.36 结束工程时报错：please log in to kill it manually
### 问题描述
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-36-1.png)
结束不了程序
### 解决方法
一般结束不了要么是程序run的时候就报错没运行起来，要么就是开发板上的进程由于某些原因杀不死。很简单你去开发板上查看程序的进程PID有没有，可以通过ps aux | grep video这样看看，有的话可以手动kill，更精确的原因可以在mind studio日志查看
方法是
1. 开发板上的系统上执行 rm /var/dlog/*
2. 然后回到你的ubuntu系统，执行你的脚本
3. 如果报错，进入mind sudio的Log-Host查看日志具体提示
