## 3.16 部署自己已经转换好的模型在Atlas 200 DK 时，需要修改样例下的哪些文件中的代码
### 问题描述
想修改sample下的objectition的样例，大致思路是修改部署脚本，将自己的转换好的模型替换掉其中的模型如（faster_rcnn)，然后推理引擎保持不变。这样可行吗？
### 解决方法
不同的模型的输入输出会不一样，替换模型需要考虑模型的输入输出是什么格式，需要在预处理做些什么，以及推理出来的数据要怎么处理，这些都是要根据实际情况来更改的，如果只是简单换掉模型，其他什么都不变，那样会推理失败。

