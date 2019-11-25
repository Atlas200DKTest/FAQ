## 4.18 如何快速停止Presenter Server进程
### 问题描述
每次停止Presenter Server进程需要找到对应的进程然后kill，效率比较低，有什么好办法快速杀死进程？
### 解决方法
将下面的代码保存为stop.sh脚本，以下的脚本是以人脸检测应用为例子，其他样例可以参考进行修改。
#!/bin/sh 
  
i=$(ps -ef | grep presenter | grep face_detection | grep -o '[0-9]\+' | head -n1) 
if [ -z "$i" ] ;then 
echo presenter sever not in process! 
exit 
fi 
kill -9 $i 
echo presenter sever stop success!
后续需要停止Presenter Server，只需执行bash stop.sh命令即可。
