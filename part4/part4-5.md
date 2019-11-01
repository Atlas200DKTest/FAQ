## 4.5 运行应用sample“通用分类网络”程序时提示has no exec file
### 问题描述
按照指导资料进行“通用分类网络”的程序执行时，运行报错：has no exec file
### 解决方法
在MindSpore Studio所在服务器中执行如下命令检查已部署的交叉编译环境。
ls -alF /usr/lib/aarch64-linux-gnu
如下图所示，表示当前MindSpore Studio所在服务器未配置交叉编译环境。
![图4-15未配置交叉编译环境](./img/4-15.png)


请参考《Ascend 310 Atlas 200 Developer Kit 使用指导》中的配置交叉编译环境章节进行交叉编译环境的配置。
已配置交叉编译环境的回显如下图所示。
![图4-16已配置交叉编译环境](./img/4-16.png)

