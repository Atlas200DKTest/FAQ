## 4.33 样例工程人体检测PresenterServer无显示
### 问题描述
样例工程正常执行，但是最后在Presenter Server上没有任何图像显示，使用本地Mp4视频或者样例中的rtsp视频流运行run脚本，但是都在PresenterServer上没有结果显示
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-33-1.jfif)
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-33-2.jfif)
1. 运行样例工程时，需要将生成的om文件在mind
studio中生成连线关系吗？还是直接跑工程就好
2. 有看到帖子说本地MP4需要放在板子上，是用读卡器放在sd卡上么？

### 解决方法
1.没有结果展示，一般是摄像头未连接、输入源无法识别这两种情况。可以查看开发板日志查询报错确认原因。
2.此问题根据截图，mp4文件是放置于Ubuntu上的，并没有上传到开发板中。MP4需要使用scp命令将文件传输到开发板上，因为执行推理时，是在开发板中进行的推理，执行run脚本时填入的mp4文件路径实际上是开发板上的对应mp4文件的路径。
具体如何登陆开发板和如何向开发板传输数据请参考：
https://ascend.huawei.com/doc/Atlas%20200%20DK/1.3.0.0/zh/zh-cn_topic_0195272404.html
https://ascend.huawei.com/doc/Atlas200DK/1.3.0.0/zh/zh-cn_topic_0183299383.html
3.RTSP运行样例时首先要确保这个RTSP流是可用的。不可以直接使用样例中的链接地址，样例中的rtsp链接地址是调试时局域网中生成的RTSP流，只可以在产生RTSP流的机器上使用。如果想使用RTSP视频流，可以使用live555制作视频流或者使用网络摄像头，使用mediaplay在本地可以正常播放后，再使用此视频流链接地址进行样例运行。

