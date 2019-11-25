## 7.8 NV21格式数据如何转换成NV12格式直接输入网络
### 问题描述
DVPP JPG解码生成YUV420SP的NV21格式的数据，但网络输入要求为YUV420SP的NV12格式的数据，应该如何进行转换？
### 问题分析
AIPP支持输入YUV420SP的NV21格式的图片，若需要将NV21转换成NV12，可以通过AIPP配置文件中的rbuv_swap_switch配置项实现通道的交换。
将rbuv_swap_switch : false修改为rbuv_swap_switch : true即可。
![图7-8-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-8-1.png)
###  解决方法
AIPP在模型转换时进行，当前Mind Studio模型转换界面中的AIPP配置支持的输入图片格式为YUV420SP_u8（NV12）和RGB888_U8（RGB），如下图所示，不支持NV21的输入格式。
![图7-8-2](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-8-2.png)
如果需要支持NV21或者BGR，需要通过命令行方式进行模型转换。
为了降低命令行方式下AIPP配置文件的配置复杂度，从Mind Studio中将AIPP的配置文件保存下来。通过Mind Studio操作界面进行模型转换，在convertModel.log日志里面会有aipp配置的打印，如下图所示，将红框中的打印信息拷贝到新文件中，例如命名为aipp.cfg。
![图7-8-3](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-8-3.png)
将保存下来的aipp.cfg文件中的rbuv_swap_switch:false修改为rbuv_swap_switch:true。
步骤 2使用命令行方式进行模型转换。
例如：
omg   --model=resnet18.prototxt --weight=ResNet-18-model.caffemodel --framework=0 --output=resnet18  --insert_op_conf=aipp.cfg
omg工具的更多参数含义请参考omg  --help。
其中参数--output就是输出离线模型的名字，输出为resnet.om。
最后把om文件拷贝到自己需要运行的位置即可。
