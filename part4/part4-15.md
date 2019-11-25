## 4.15 应用程序中如何使用opencv
### 问题描述
请问应用程序中如何使用opencv?
### 解决方法
C++代码可以直接使用opencv，安装完Mind Studio后，会自动部署opencv的头文件，用户C++代码中可直接引用，opencv的头文件路径为DDK路径的/ddk/include/third_party/opencv/include/目录下。
opencv的使用示例可参考人脸识别应用：https://github.com/Ascend/sample-facialrecognition，其中face_feature_mask/face_feature_mask.cpp含有opencv的调用代码。
非c++环境下用户需要自己安装opencv，例如python，Atlas 200 DK上是没有python的opencv的，用户若需要在Atlas 200 DK上调用python的opencv，需要自行安装arm版的opencv
