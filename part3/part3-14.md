## 3.14 将caffe训练后的模型通过换后的OM模型放入到sample_objectdetection工程中编译运行，提示以下错误
### 问题现象
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-14-1.png)

### 问题处理
TENSOR’S SIZE错误，新的模型需要1组数据输入，原模型需要2组数据输入，导致推理失败，将代码中送入推理模块的INPUT数据改成一组数据，就可以推理成功了

