## 3.21 年龄预测模型在C10版本精度正常，在C30版本精度损失很大
### 问题描述
年龄识别应用，因为觉得在c10版本执行运行速度较慢，所以切换至c31版本尝试。但是转c30版本后有较大精度损失，预测的年龄普遍在27-28左右
### 解决方法
在c10版本和c30版本是同一套代码，唯一不同的是模型不同，于是猜想模型转换时c30版本某个算子或某些算子约束改变，导致模型精度损失。先要拿到代码和模型，包括样例代码，tensorflow模型，tensorflow训练代码和测试代码，使用的测试集。
1) 问题复现。
	首先修改classification代码，修改参考colorization前处理，后处理部分把得到的概率分布乘以他们的序号，得到年龄的期望值，即预测的年龄。用pb模型转davinci模型，加载转换好的davinci模型，用测试数据集进行测试。选取image_145.jpg，该输入图片的实际年龄为53岁，但是预测的年龄为30岁左右，存在较大偏差，与tensorflow预测结果（51岁左右）偏差较大。问题复现。
2) 问题定位
	根据文档https://ascend.huawei.com/doc/Atlas200DK/1.3.0.0/zh/zh-cn_topic_0165968579.html可以通过—out_nodes参数指定输出节点。于是先用netron读取原pb模型，在模型中用二分法截断模型输出找到750版本和891版本差异较大的算子层，用二分法逐层比较找到起始差异点进行分析。把out_nodes打印数据保存在txt里，750和891各存一份txt数据，写个Python脚本分析差异量：
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-21-1.png)
输出两个版本对应算子运算结果中，该层输出结果的最大值，最小值，对应数据差值的绝对值的最大值，以及数值大小想差0.1以上的数量。经过层层分析，最终定位到首层算子，RealDiv算子
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-21-2.png)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-21-3.png)
可以看到该层算子的输入格式是NC1HWC0，向钟永根请教该层算子约束的750和891版本差异，钟永根建议说，tensorflow模型在不开启aipp时需要自行做nhwc转nchw的操作，先尝试着做数据格式转换，排除下这个问题
问题解决：
	在前处理地方，opencv读取图片后把数据拷贝出来谢了个代码片段做数据格式转换：
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-21-4.png)
经验证，格式转换后精度上有了很大提升，image_145在891版本上预测结果为51岁，已经很接近真实年龄，与tensorflow预测结果一致，至此，问题已定位出来，并得到解决
问题解决的优化
	这样自行做数据格式转换效率可能较低，于是尝试用aipp来做。
a) 模型转换时，输入图像格式选择为RGB888_U8
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part3/img/3-21-5.png)
此时输入数据类型为int8，不需要再转float
b) 使用omg工具命令行转模型时，通过指定参数—input_format=”NCHW”，aipp关闭。此时推理输入NHWC格式数据即可，不过此时输入数据类型为float。
问题解决后续：
	用户按照设置输入图像格式的方式转模型，得到了相同的预测精度，且运行速度提升了不少。

