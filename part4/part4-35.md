## 4.35 DDK样例 classify_net 运行没有结果
### 问题描述
用户反馈：运行DDK样例classify_net，没有报错，但是没有result file

========== Test Start ==========
File ./test_data/resnet-18/model/ResNet-18-model.om is ready

### 问题分析
将用户的版本文件在本地运行，可以正常出运行结果
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-35-1.png)

### 问题处理：
请用户确认版本: 
单板 cat /etc/sys_version.conf 看系统版本，版本为750，
主机查看 DDK版本为891，两者不匹配。单板版本升级到891后，可正常运行出结果

