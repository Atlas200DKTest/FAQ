## 5.16 vgg16运行失败
### 问题描述
vgg16网络可以正常转换模型，转换指令为
omg --model vgg16.prototxt --weight vgg16.caffemodel --framework 0 --inser_op_conf aipp.cfg --input_shape 
"data:32, 3, 224,224"
但是运行时出现报错
framework/domi/ome/model_manager/model_manager.cpp:706:"data len(4816896) does not match the model data len(150528),

aipp.cfg为：
aipp_op {
    aipp_mode: static
    input_format : RGB888_U8
    csc_switch : false
    rbuv_swap_switch : false
    matrix_r0c0 : 76
    matrix_r0c1 : 150
    matrix_r0c2 : 30
    matrix_r1c0 : 0
    matrix_r1c1 : 0
    matrix_r1c2 : 0
    matrix_r2c0 : 0
    matrix_r2c1 : 0
    matrix_r2c2 : 0
    output_bias_0 : 0
    output_bias_1 : 0
    output_bias_2 : 0
}
生成的om仅要求3*224*224=150528，这是为什么？其他的模型比如resnet、googlenet都是正常的，只有vgg出现这个问题

### 解决方法
把protxt里面的input_param的N改成32就可以了
