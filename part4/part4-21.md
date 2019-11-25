## 4.21 样例程序中RTSP视频流无法使用
### 问题描述
运行车辆检测应用程序时，RTSP视频流运行失败，界面不展示。
### 可能原因
RTSP视频流运行失败，存在以下两种原因：
视频流存在问题，
应用程序运行方式存在问题。
首先在媒体播放器中播放RTSP视频流，成功，证明RTSP视频流不存在问题，所以考虑是程序的运行方式存在问题。
检查config文件，发现RTSP视频流为channel1，这证明没有使用空格对channel1进行占位，从而导致运行失败。
### 解决方法
执行run脚本时，RTSP视频流需要使用channel2，此时需要使用空格对channel1进行占位，否则程序无法识别当前是MP4文件还是RTSP视频流。
例如：
bash run_videoanalysiscarapp.sh 192.168.1.2 video " " "rtsp://192.168.2.37:554/cam/realmonitor?channel=1&subtype=0" &
