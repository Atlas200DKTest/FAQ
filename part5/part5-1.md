## 5.1 SrcEngine, InferenceEngine与DestEngine的开发思路是什么？
	在MindSpore Studio的画布上展示的几乎每一个节点（除了模型和数据集）都是一个引擎，所有引擎构成了一个图。
	我们的应用框架启动时就是将图初始化好，然后我们编写代码向第一个引擎灌注数据，一旦有数据进去，引擎便开始工作，数据从一个引擎进入、处理，然后输出至下一个引擎；下一个引擎接到上一个引擎的输入，又开始工作，如此执行下去直到最后一个引擎处理完毕给出结果，单次执行算是结束。
	正常情况下我们是首先准备好数据集，然后将数据集一帧一帧的灌进预处理引擎，预处理结束将数据交给模型推理引擎，模型推理结束将数据交给后处理引擎，完成一次完整的推理过程。
预处理一般我们会将输入处理成模型需要的数据格式，如果是CV类应用，可调用我们自研的DVPP进行图像的预处理，如裁剪、格式转换等；
	推理就是拿到上一层处理结果来调用模型进行推理。
	后处理是拿到上一层的推理结果进行后续的动作，可以直接将结果打印个日志（输出到文件中），如果结果是矩形的两点坐标，可以通过后处理在原图上根据两点坐标画个矩形展示出来等等，根据需要进行编写即可。

