## 3.6 Caffe模型转换时提示不支持layers
### 问题描述
caffe模型转换过程中报错：
The weight file is consisted of layers-structure  
which is deprecated in caffe and unsupport in OMG. It is recommended to convert layers-structure  
to layer-structure by caffe tool.
### 解决方法
此模型文件中存在模型转换工具不支持的layers，需要将模型文件中的layers改成layer，必要时修改layer的属性。
caffe提供了layers到layer格式转换的工具，为GitHub上\caffe-master\tools\upgrade_net_proto_binary.cpp与\caffe-master\tools\upgrade_net_proto_text.cpp。

