## 4.14 如何替换应用样例中的模型文件
### 问题描述
在FaceDetection应用样例中修改模型文件为fasterrcnn-vgg16，并修改相应输入参数，运行时报graph生成失败的错误。
如下所示：
![4-14-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-14-1.png)
请问"HCSService::GetHC**ecutorByDevice we don't support this device whose device code is 4!"是什么意思，如何解决？
### 解决方法
步骤 1请确保使用的“*.om”模型文件的版本与运行当前应用程序的Mind Studio的版本相同，不同版本的Mind Studio的模型不能混用。
步骤 2修改代码文件中的graph_deploy.config文件，请将此文件中的模型文件名称替换成自己的模型文件名称，并将batch_size修改为模型转换时设置的Input Shape中的N，如下图所示。
图5-22模型转换配置
![4-14-2](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-14-2.png)
步骤 3将*.om模型文件拷贝到graph_deploy.config文件所在的同级目录中。
步骤 4修改实现代码中的模型输入部分，以人脸识别为例，如下图所示。
![4-14-3](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-14-3.png)
替换模型的输入大小在模型转换的时候确定，即：C=kRgbChannel，H=kResizeImgHeight，W=kResizeImgWidth。
步骤 5执行部署及运行脚本。
