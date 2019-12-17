## 3.18 Mind Studio tensorflow的pb模型转OM模型出错"Parse Params for node input failed"
### 问题现象
[ERROR] FMK:2019-11-11-14:41:40.037.844 CheckInputShape:framework/domi/omg/../omg/parser/tensorflow/tensorflow_data_parser.cpp:155:"parse data node input: shape contains placeholder ,but not designated by user Error Code:0x3000001()"
[ERROR] FMK:2019-11-11-14:41:40.037.873 ParseParams:framework/domi/omg/../omg/parser/tensorflow/tensorflow_data_parser.cpp:23:"input node input :check user designated input shape not match input shape defined in model"
[ERROR] FMK:2019-11-11-14:41:40.037.902 AddNode:framework/domi/omg/../omg/parser/tensorflow/tensorflow_parser.cpp:87:"Parse Params for node input failed"
[ERROR] FMK:2019-11-11-14:41:40.043.290 Generate:framework/domi/omg/omg.cpp:730:"OMG model parse ret fail. Error Code:0x3000001()"
[ERROR] FMK:2019-11-11-14:41:40.043.939 main:framework/domi/omg_main/main.cpp:791:"OMG Generate execute failed!!"
OMG generate offline model failed. Please see the log or pre-checking report for more details.
[INFO] RUNTIME:2019-11-11-14:41:40.048.719 1077 runtime/feature/src/driver.cc:57 ~Driver:deconstruct driver
### 解决方法
在转模型的时候需要自行点击Input Shape旁边的加号，填上输入节点的相关信息。输入节点信息可通过netron、tensorboard等软件查看pb的网络结构图获取。。

