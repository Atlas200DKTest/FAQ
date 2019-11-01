## 1.3  MindSpore Studio IP地址更换后，使用新IP地址登录失败
### 问题现象
更换IP地址后，修改了~/tools/scripts下的env.conf文件并重启网络，登录MindSpore Studio还是失败。

### 解决方法

1. 检查env.conf文件，确认配置的ip没有问题。
2. 重启MindSpore Studio，登录成功。
#### 说明
IP地址更改后，需要重启MindSpore Studio，否则服务端不识别更改后IP地址。
