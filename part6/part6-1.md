## 6.1 如何上传文件到Host侧
​	Atlas 200 DK中开发者板（Host）的默认IP地址为192.168.1.2（USB连接方式）或者192.168.0.2（NIC连接方式），MindSpore Studio（UI Host）中一般存在2个IP地址，访问MindSpore Studio Web界面的IP地址以及与开发者板通信的IP地址（与开发者板在同一网段），如图6-1所示。
MindSpore Studio的运行用户为用户自定义的MindSpore Studio的安装用户，Host侧的运行用户为HwHiAiUser。
![图6-1Atlas 200 DK UI Host与Host连接示例](./img/6-1.png)


​	AI加速云服务器中，MindSpore Studio（UI Host）与Host部署在同一服务器中，访问IP地址相同，但运行用户不同。MindSpore Studio的运行用户为用户自定义的MindSpore Studio的安装用户，Host侧的运行用户为HwHiAiUser。
![图6-2AI加速云服务器UI Host与Host连接示例](./img/6-2.png)


将文件从UI Host上传到Host的可以使用scp命令，示例如下所示。
在UI Host中执行如下命令：
scp /filepath/filename HwHiAiUser@host_ip:/home/HwHiAiUser/filepath
例如将UI Host中的/home/ascend/car.mp4文件拷贝到Host侧的/home/HwHiAiUser/sample路径下。
scp /home/ascend/car.mp4 HwHiAiUser@192.168.1.2:/home/HwHiAiUser/sample

