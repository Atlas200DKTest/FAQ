## 5.14 运行tensorflow 报错：tf.gfile.Exists is deprecated
### 问题描述
运行 tensorflow 代码报错 tf.gfile.exists is deprecated，please use tf.io.gfile.exists instead 


![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-14-1.png)


### 解决方法
用tf.io.gfile.exists 替换tf.gfile.Exists,重新编译
