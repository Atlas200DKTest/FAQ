## 3.9 模型转换时宽和高进行128x16对齐了吗
### 问题描述
以人脸检测模型为例，若模型转换时界面只填了1, 3, 300, 300，是否不需要宽和高的字节对齐？
### 解决方法
模型转换时AIPP开关默认是打开的，展开Optional Options，可看到如下参数：
![图3-8-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-8-1.jpg)
Input Image Size进行了128x16的对齐。
如果将Input Image Preprocess关闭，则运行人脸检测程序会报错：
![图3-8-2](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-8-2.jpg)
因为此时模型需要的数据长度为1*3*300*300*4(float类型)=1080000，而人脸检测sample代码送入推理引擎的数据长度为384*304*1.5（YUV）=175104，两者长度不匹配，推理失败。
