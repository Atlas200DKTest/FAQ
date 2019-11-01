## 4.10 人脸检测应用程序停止异常
### 问题描述
执行bash stop_facedetectionapp.sh 192.xxx.xxx.xxx命令停止人脸检测应用时，出现如下错误：
 kill 192.xxx.xxx.xxx:ascend_facedetectionapp running failed, please login to kill it manually.
### 解决方法
#### 步骤 1 
	确认执行停止命令时，输入的Atlas 200 DK开发者板的IP地址正确。
若使用USB方式连接UI Host，默认IP地址为192.168.1.2；若使用NIC方式连接UI Host，默认IP地址为192.168.0.2。
若使用的Atlas 200 DK开发者板的IP地址正确，请执行步骤2手工停止应用进程。
若使用的Atals 200 DK开发者板的IP地址错误，请输入正确的IP地址重新执行bash stop_facedetectionapp.sh 192.xxx.xxx.xxx命令。
#### 步骤 2 
	手工在Atlas 200 DK开发者板上停止人脸检测应用进程。
1. 在UI Host上以HwHiAiUser用户以SSH方式登录Atlas 200 DK开发者板。
2. 执行如下命令查看人脸检测应用的进程PID。
ps -ef | grep face
3. 执行如下命令，停止人脸检测应用进程。
kill -9 人脸检测应用的进程PID
----结束
