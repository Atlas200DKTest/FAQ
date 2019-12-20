## 4.31 将人脸检测示例部署在Mind Studio的过程中手动添加了channel.h文件、errors.h文件到项目中，执行报错找不到该文件？
### 问题描述
运行人体检测样例是，在进行适配替换后再重复运行，Presenter Server界面卡死。

![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-31-1.png)

### 解决方法
查看编译时的打印信息中aarch64-linux-gnu-g++ -c -I XXXX 后面一长串那个，把这个信息拷贝出来，看下ascend_ddk的完整路径，然后在那个路径下找找有没有报错的头文件，然后根据情况更改makefile中的路径。
