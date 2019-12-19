## 7.11 yolov3模型转化失败，报错read proto from text ret fail
### 问题描述：
转换yolov3模型失败，报错
read proto from text ret fail, model path: /home/ascend/tools/che/model-zoo/my-model/.temp/yolov3-spp_videostructure_c15_test/yolov3-spp_videostructure_c15_test.prototxt
如图所示

![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-11-1.jfif)
### 解决方法
根据报错日志分析，读取prototxt文件的时候已经报错了。转换模型时，需要读取prototxt和caffemodel文件。这两个文件的属主需要是Mindstudio安装用户，同时要具有可读写权限，使用chmod给文件加上读写权限再重新转模型
