## 3.15 使用C32 Mind Studio的模型转换时的参数配置问题
### 问题描述
1）之前版本(Web版)的Mind Studio模型转换功能，AIPP不需要手动输入对齐后的图片的宽高以及色域配置
2）C32 的Mind Studio的模型转换，AIPP需要手动输入对齐后的图片的宽高以及模型的色域配置
### 解决方法
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-15-1.png)
Input Image Format输入的宽高要保证128和16对齐。
Model Image Format的格式根据模型要求的输入格式，手动选择一下。

