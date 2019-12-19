## 5.11 命令行跑profiling 报 no exec file
### 问题描述
命令行方式跑pfofiling，报no exec file

![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-11-1.png)


### 问题分析
定位发现profiling参数 --app 的app名字必须是main，否则找不到app。
### 解决方法
修改makefile，使产生的app 名字为main，重新运行profiling,不报该错误

