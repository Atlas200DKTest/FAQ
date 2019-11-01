## 3.5 ShuffleNet模型转换时无法进行8bit量化
### 问题描述
ShuffleNet模型转换的时候选择8bit量化后模型转换失败，convertModel.log日志如下：
[ERROR] FMK:2019-05-23-10:20:29.220.547 CreateOp:framework/domi/calibration/op/op_factory.cpp:20:"OpFactory::CreateOp: Not supported OP, type = ShuffleChannel"
如下图所示：
![图3-8模型转换失败日志](./img/3-8.jpg)


### 解决方法
shufflenet模型中的shuffleChannel算子暂时还不支持量化。
只有当算子支持量化时，才可以使用exclude_op选项将算子加入黑名单使之不进行量化。
当前只支持量化的算子有Convolution、Full Connection与ConvolutionDepthwise。

