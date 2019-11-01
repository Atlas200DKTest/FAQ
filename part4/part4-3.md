## 4.3 应用faster-R-cnn网络模型执行目标检测报no result file
### 问题描述
应用MindSpore Studio模型导入功能成功导入目标检测模型faster-R-CNN。
应用faster-R-CNN网络进行编排，编排流程如图4-5所示。
![图4-5目标检测编排流程](./img/4-5.png)


程序运行时出现如图4-6所示错误信息。
![图4-6目标检测编排流程](./img/4-6.png)


或者运行结束后单击“FasterRCNNPostProcess”节点，选择“Image Result”，出现如图4-7所示错误。
![图4-7流程编排结果显示错误](./img/4-7.png)


### 解决方法
#### 问题1：流程编排不对
按照图4-8所示进行目标检测流程编排。
![图4-8目标检测网络编排流程](./img/4-8.png)


其中MindInferenceEngine的默认输入端口个数为2，需要修改此节点的InputNum值为3，修改方法参见图4-9。
![图4-9MindInferenceEngine节点输入参数设置](./img/4-9.png)


FaseRCNNImageInfo为MindSpore Studio内置的仅用于FasterRcnn网络的输入图片处理Engine，作为MindInferenceEngine的第三个输入。
#### 问题2：图片预处理节点的Resize属性值设置不正确，未按照模型要求的宽与高进行设置。
a.查看模型要求宽与高，具体查看方法请参见步骤1。
b.设置ImagePreProcess节点的Resize属性的width与height为模型要求的宽和高，如图4-10所示。
![图4-10ImagePreprocess节点Resize设置](./img/4-10.png)



