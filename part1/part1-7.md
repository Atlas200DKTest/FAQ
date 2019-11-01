## 1.7 MindSpore Studio无法正常启动--删除
### 问题描述
Mongodb服务没有启动成功或启动失败。
#### 可能原因1
通过如下命令查看进程，Mongodb进程不存在：
ps -ef | grep mongod
#### 解决方法1
若进程不存在，则进入“vendor/mongodb/mongodb-linux-x86_64-3.0.6/bin”目录，执行如下命令：
./mongod --fork --dbpath /data/db --rest --syslog
#### 可能原因2
启动Mongodb报错，报错现象如下所示：
ERROR:child process failed, exited with error number 100
#### 解决方法2
该问题可能的原因是上一次启/停mongdob异常，导致mongodb数据库锁死。
以MindSpore Studio安装用户登录后台服务器，在~/tools/db目录下查看是否存在mongod.lock，若存在，则说明确实由于数据库死锁，删除该文件重新安装即可，如果不生效，则删除安装路径下的整个db文件夹。
