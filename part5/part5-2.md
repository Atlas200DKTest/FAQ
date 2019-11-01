## 5.2 通过界面进行模型转换时的DetectionOuput的含义
通过MindSpore Studio界面进行模型转换时，用户可能会遇到如下界面：
![模型转换](./img/5-1.png)
此时你需要在右侧的下拉选择框中根据你自己的网络选择一个算子。
原因为不同网络类型的DetectionOutput算子的定义不同，当您的模型文件中含有DetectionOutput算子时，模型转换时OMG不知道应该用什么网络的DetectionOutput算子去转换这一层，所以需要用户根据自己的网络选择一个DetectionOutput，即在OMG内部将此算子根据网络进行重命名。

