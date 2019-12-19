## 5.7 在Ubuntu虚拟机中使用pip安装numpy失败
### 问题描述
在虚拟机中使用pip安装numpy失败，报错如下图所示：
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-7-1.png)
### 解决方法
1.首先对pip进行升级，输入命令pip install --upgrade pip
之后检查pip的版本号：输入命令pip --version 报错：	Traceback (most recent call last):
File “/usr/bin/pip”, line 9, in 
from pip import main
此为pip升级之后的BUG。
2.超级用户下编辑/usr/bin/pip文件，修改如下：
原始/usr/bin/pip文件：
from pip import main
if __name__=='__main__':
sys.exit(main())
修改为：
from pip import __main__
if __name__=='__main__'
sys.exit(__main__._main())
3.再次输入pip --version pip的版本已经升级到19.3.1
4.使用pip install numpy --user安装numpy成功

