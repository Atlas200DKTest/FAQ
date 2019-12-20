## 4.29 重复运行样例后失败
### 问题描述
在调试软件过程中，将其中一个没有参与软件功能engine从graph.config去掉编译运行出错。
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-29-1.png)
### 解决方法
cmakelist.txt中对应的engine必须和graph.config中对应，就是一个engine如果不参与工程编译，需要将engine中对应的engine定义删除，engine链接关系里面如果有链接这个engine也要做对应修改，不要链接此engine.

