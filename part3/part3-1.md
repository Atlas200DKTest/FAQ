## 3.1 模型转换时报It is recommended to convert layers-structure to layer-structure by caffe tool错误
### 问题描述
从https://github.com/BVLC/caffe/tree/master/models/bvlc_googlenet下载了googlenet的prototxt与caffemodel，导入时失败，如图3-1所示。
![图3-1模型转化失败](./img/3-1.jpg ''图3-1'')


“converModel.log”日志报错如下：
[ERROR] FMK:2018-12-22-23:47:48.147.318 ConvertNetParameter:framework/domi/omg/parser/caffe/caffe_parser.cpp:776:"The weight file is consisted of layers-structure which is deprecated in caffe and unsupport in OMG. It is recommended to convert layers-structure to layer-structure by caffe tool. Error Code:0xFFFFFFFF(failed)"
### 解决方法
产生此错误原因为模型文件版本过低，需要用Caffe提供的工具将模型prototxt文件与caffemodel文件升级为最新版本。Caffe工具可从Link获取。
#### 步骤1
	用户自行下载Caffe的upgrade_net_proto_text工具与upgrade_net_proto_binary工具至MindSpore Studio所在服务器任一目录。
#### 步骤 2
	使用upgrade_net_proto_text工具升级prototxt。
upgrade_net_proto_text model_old.prototxt model_new.prototxt
#### 步骤 3
	使用upgrade_net_proto_binary升级caffemodel。
upgrade_net_proto_binary model_old.caffemodel model.new.caffemodel
#### 步骤 4
使用转换后的protoxt文件与caffemodel文件重新进行模型导入。
----结束
