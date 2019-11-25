## 4.17 运行人脸检测的deploy.sh时提示IDE-daemon-client错误
### 问题描述
运行人脸检测的deploy.sh脚本时提示IDE-daemon-client未找到的错误，但是在对应的目录下存在此工具，切换此工具所在目录，IDE-daemon-client命令是可用的。
### 解决方法
使用软连接可以解决此问题。
在DDK所在路径的/ddk/bin/x86_64-linux-gcc5.4目录下执行如下命令创建软连接：
ln -s /home/xxx/tools/che/ddk/ddk/bin/x86_64-linux-gcc5.4/IDE-daemon-client /usr/lib/IDE-daemon-client
