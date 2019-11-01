## 3.4 Offline Model导入Davinci模型文件时提示Not a legal om file
### 问题描述
在“Tool > Conver Model”中选择“Offline Model”导入本地已经转换好的Davinci模型时报如下错误：
![图3-7Offline Model导入Davinci失败](./img/3-7.jpg)


### 解决方法
如果用户是直接使用Git或者SVN下载的模型文件，默认都是经过压缩的文件，因此要检查下载的*.om文件是否被正确下载，文件大小与原始文件大小是否一致。

