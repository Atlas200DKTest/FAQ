## 7.13 yolov3样例中general_post.cpp定义的anchors是什么，如何定义的
### 问题描述
仿照Atlas200DK-sample-objectdetctionbyyolov3-master，修改源码进行适配，编译成功，但是detect的时候显示segmentation falt，排查发现是因为anchors有修改导致，general_post.cpp中的anchors顺序定义是什么
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-13-1.jfif)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-13-2.jfif)
### 解决方法
anchors的含义可以参考：https://blog.csdn.net/cgt19910923/article/details/82154401
这里anchors的顺序是和kGridSize中的参数对应的。kGridSize包含三个参数，分别为13,26,52。这里的13代表将当前图片划分为13*13个网格，26和52以此类推。然后在这些网格中再使用KGridSize中的三个坐标点所绘制的矩形框中判断这个网格中是否有这个物体。
anchors中每六个参数为一组对应kGridSize中的参数，当KGridSize取值为13时，图片被划分成169个矩形框，anchors中对应有116，90,156,198,373,326这六个参数，代表每个矩形框中判断116,90、156,198、373,326（第一位代表长，第二位代表宽，以每个网格中心点为中心）这三个矩形中图片是否为某一类物体
这个参数是在模型训练时决定的，如果没有替换模型，修改后是无法运行的

