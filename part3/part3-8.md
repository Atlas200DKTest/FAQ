## 3.8 模型转换时出现dev memory malloc error的错误
### 问题描述
用户在进行faster rcnn_vgg16和ssd的模型转换时（使用的github中的原始模型文件），打印日志如下：
[INFO] FMK:2019-09-12-04:53:55.031.016 BuildModelDef:framework/domi/omg/../omg/model/model_builder.cpp:2464:"weight_offset_: 123655680" 
[INFO] FMK:2019-09-12-04:53:55.031.048 BuildModelDef:framework/domi/omg/../omg/model/model_builder.cpp:2466:"Set event num: 0." 
[INFO] FMK:2019-09-12-04:53:55.031.099 SyncInputOutputInfoToOriginalGraph:framework/domi/omg/../omg/model/model_builder.cpp:2522:"Start to sync input&output memory info to original graph" 
[INFO] FMK:2019-09-12-04:53:55.111.235 SyncInputOutputInfoToOriginalGraph:framework/domi/omg/../omg/model/model_builder.cpp:2558:"Call Fusion Engine success, but there is no fusion op" 
[INFO] FMK:2019-09-12-04:53:55.111.584 SyncWorkspaceInfoToOriginalGraph:framework/domi/omg/../omg/model/model_builder.cpp:2595:"Start to sync workspace memory info to original graph" 
[INFO] FMK:2019-09-12-04:53:55.114.182 SyncWorkspaceInfoToOriginalGraph:framework/domi/omg/../omg/model/model_builder.cpp:2630:"Call Fusion Engine success, but there is no fusion op" 
[INFO] FMK:2019-09-12-04:53:55.117.116 GetModelTask:framework/domi/omg/../omg/model/model_builder.cpp:3195:"Begin to GetModelTask..." 
[INFO] FMK:2019-09-12-04:53:55.117.454 GetTaskInfo:framework/domi/omg/../omg/model/task_generator.cpp:100:"Begin to Get TaskInfo." 
[INFO] FMK:2019-09-12-04:53:55.224.966 LoadCustomAiCpuSo:framework/domi/omg/../omg/model/task_generator.cpp:304:"no aicpu so in model! Check result false, status: 0x0 " 
[INFO] RUNTIME:2019-09-12-04:53:55.379.772 69671 runtime/feature/src/logger.cc:236 DevMalloc:dev memory alloc, size = 545656832, type = 1 
[ERROR] RUNTIME:2019-09-12-04:53:55.522.058 69671 runtime/feature/src/logger.cc:240 DevMalloc:dev memory alloc error, errno = 2 
[ERROR] FMK:2019-09-12-04:53:55.522.553 GetTaskInfo:framework/domi/omg/../omg/model/task_generator.cpp:116:"Call rt api failed, ret: 0x2" 
[ERROR] FMK:2019-09-12-04:53:55.653.618 GetModelTask:framework/domi/omg/../omg/model/model_builder.cpp:3204:"GetTaskInfo Failed!" 
[ERROR] FMK:2019-09-12-04:53:55.745.584 FuseGraphAndGetTaskInfo:framework/domi/omg/../omg/model/model_builder.cpp:3860:"Get model task data failed!" 
[ERROR] FMK:2019-09-12-04:53:55.847.029 Generate:framework/domi/omg/omg.cpp:819:"OMG builder FuseGraphAndGetTaskInfo() return fail." 
[ERROR] FMK:2019-09-12-04:53:56.772.128 main:framework/domi/omg_main/main.cpp:791:"OMG Generate execute failed!!" 
OMG generate offline model failed. Please see the log or pre-checking report for more details.
### 解决方法
用户使用的虚拟机内存为2G，首先怀疑为虚拟机的内存问题，因为Mind Studio依赖的环境内存大于等于4G。
1. 首先使用小模型文件进行转换，例如使用人脸检测模型（人脸检测模型文件大小为10M，fasterrcnn模型文件大小为130M）进行转换，转换成功。
2. 请用户将内存修改为4G，再次尝试fasterrcnn、SSD的模型转换，转换成功。
