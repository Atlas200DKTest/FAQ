## 4.28 在运行mindstudio时，切换其他工程，运行报错。
### 问题描述
在调试软件过程中，例如facedetection，在运行过程中，mindstudio切换目标检测，编译运行，此时报错。
### 解决方法
原来的present server还在运行，所以新的工程无法运行present server，用 
ps -ef | grep present检查，kill 掉原来工程的present server id，然后新的工程重新运行就可以了。
