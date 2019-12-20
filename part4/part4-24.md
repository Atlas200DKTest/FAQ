## 4.24 跑社区案例人脸检测时，到build的一步报错,无法进行编译
### 问题描述
是制卡用过不同的arm包，未进行同步依赖库就直接进行build。
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-24-1.png)
### 解决方法
然后在tools下的Device Management，重新进行添加开发板同步依赖库，在build
其中1.31.T15.B150为对应的DDK版本
