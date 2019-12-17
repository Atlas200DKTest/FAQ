## 3.23 caffe 模型转换om报：Get model input shape error
### 问题描述
caffe prototxt两个输入，转换模型时报错

![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-23-1.png)
### 问题分析
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-23-2.png)
prototxt 如上图，caffe将两个input写在一起，而om不支持这个格式，需要分开写。
### 解决方法
name: "sknet50_basic"
input: "data"
input_shape {
      dim: 32
      dim: 3
      dim: 224
      dim: 224
}
input: "label"
input_shape {
      dim: 32
}
prototxt修改为如上格式，模型可以转换。

