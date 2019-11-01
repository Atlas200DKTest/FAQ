## 1.2 MindSpore Studio安装完成无法登录，界面报错IP不正确
### 问题现象
MindSpore Studio安装完成后，登录时界面报如下错误：
![图1.1 MindSpore Studio登录错误界面](./img/1-1.jpg ''图一'')

### 解决思路
连接异常，检查ip配置，发现ip配置无误。发现登录网址时，未输入https://。该情况和默认输入http://一样，无法被识别。
以https://****:8888/dashboard/#/重新登录，登录成功。
