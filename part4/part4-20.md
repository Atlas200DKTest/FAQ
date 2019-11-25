## 4.20 重复运行样例后失败
### 问题描述
运行人体检测样例是，在进行适配替换后再重复运行，Presenter Server界面卡死。
### 解决方法
重复运行应用程序时，设置的在Presenter Server展示的名称需要保持唯一，例如对于如下命令
bash run_videoanalysispersonapp.sh 192.168.1.2 video "/home/HwHiAiUser/sample/person.mp4" &
video需要重新命名，在Presenter Server展示界面中需要保持唯一。
