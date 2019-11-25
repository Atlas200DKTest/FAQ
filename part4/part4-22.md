## 4.22 车辆检测应用启动报channel is not open, send message failed错误
### 问题描述
部署完车辆检测应用后，启动Presenter Server成功，但是运行无结果，查看日志发现以下报错：
[ERROR]     2019-09-18-10:52:00.816.576APPSendDetectionImageascend_videoanalysiscarappserver 
response failed, error code=6,[video_analysis_post.cpp:269:SendDetectionImage], 
Msg: the args not right 
[ERROR]     
2019-09-18-10:52:00.816.797APPVideoAnalysePostascend_videoanalysiscarappSendDetectionImage 
failed,error code: 3,[video_analysis_post.cpp:369:Process], Msg: the args not 
right 
[ERROR]     
2019-09-18-10:52:00.817.176APPascend_videoanalysiscarapp[src/ascenddk/presenter/agent/util/socket_utils.cpp:202] 
socket closed ,[src/ascenddk/presenter/agent/util/socket_utils.cpp:202:ReadN], 
Msg: the args not right 
[ERROR]     
2019-09-18-10:52:00.817.266APPascend_videoanalysiscarapp[src/ascenddk/presenter/agent/connection/connection.cpp:146] 
Failed to read message header ,[src/ascenddk/presenter/agent/connection/connection.cpp:146:ReceiveMessage], 
Msg: the args not right 
[ERROR]     
2019-09-18-10:52:00.817.337APPascend_videoanalysiscarappsend car result 
failed, error code=2,object_id = 
car_1,[video_analysis_post.cpp:321:SendCarInfo], Msg: the args not right 
[ERROR]     2019-09-18-10:52:00.817.411APPVideoAnalysePostascend_videoanalysiscarappSendCarColor 
failed,error code: 3,[video_analysis_post.cpp:392:Process], Msg: the args not 
right 
[ERROR]     
2019-09-18-10:52:00.842.271APPascend_videoanalysiscarapp[src/ascenddk/presenter/agent/channel/default_channel.cpp:211] 
Channel is not open, send message failed 
,[src/ascenddk/presenter/agent/channel/default_channel.cpp:211:SendMessage], 
Msg: the args not right 
[ERROR]     
2019-09-18-10:52:00.842.418APPascend_videoanalysiscarappsend car result 
failed, error code=2,object_id = 
car_1,[video_analysis_post.cpp:321:SendCarInfo], Msg: the args not right 
[ERROR]     
2019-09-18-10:52:00.842.513APPVideoAnalysePostascend_videoanalysiscarappSendCarType 
failed,error code: 3,[video_analysis_post.cpp:380:Process], Msg: the args not 
right 
[ERROR]     
2019-09-18-10:52:00.852.754APPCarPlateRecognitionascend_videoanalysiscarappinput 
object image is empty!,[car_plate_recognition.cpp:448:Process], Msg: the args 
not right
![4-22-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-22-1.png)
### 可能原因
查看Presenter Server相关配置，配置正确，相关库文件也完整。
因为错误原因是后处理数据发送失败，推测是否是Presenter Server存储数据的路径没有写权限导致发送数据失败。
查看设置的目录文件权限，存储数据的目录属于root用户组，而Mind Studio安装用户无写权限。
![4-22-2](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-22-2.png)
### 解决方法
修改存储数据的目录的用户属组，样例即可正常运行。
