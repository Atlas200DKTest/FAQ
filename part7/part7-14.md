## 7.14 推理100次后，程序不退出
### 问题描述
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-14-1.png)
### 问题现象
用户为了计算100次的推理的平均时间，修改inference引擎的推理代码，调用100次；同时修改了main.cpp中的flag =100，分析代码
      首先：处理最后一帧图片，会发送结束标记：
  image_handle->is_finished = true;
  if (SendToEngine(image_handle)) {
    return HIAI_OK;
  }

其次：main函数中收到消息，操作flag
HIAI_StatusT CustomDataRecvInterface::RecvData(
    const std::shared_ptr<void>& message) {
  // no need to read any message, only decrease flag
  mt.lock();
  flag--;
  mt.unlock();
  return HIAI_OK;
}
主程序代码中，flag=0 时进程才会退出。
for (;;) {
    // finished, break
    if (flag <= 0) {
      break;
    } else {
      usleep(kSleepInterval);
    }
  }
虽然推理调用了100次，但是整个程序只会发送一次结束标记，回调函数RecvData只会调用1次。
### 解决方法
修改main的flag =1，程序正常退出。

