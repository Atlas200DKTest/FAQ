## 5.13 如何实现engine多输出和多输入？
要实现engine多端口输入/输出，首先在对应engine头文件处把INPUT_SIZE/OUTPUT_SIZE设置为需要的数量。以人脸识别样例为例，face_detection engine有三个输入端口，设置如下：
#define INPUT_SIZE 3
#define OUTPUT_SIZE 1

![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-13-1.png)

然后在graph.config文件中配置engine之间连接（配置connects）
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-13-2.png)
其中446即为face_detection的engine id（三个端口中一个为模型输入）
实现发数据时候，在SendData指定目标端口号
   hiai_ret = SendData(kSendDataPort, "FaceRecognitionInfo",
                        static_pointer_cast<void>(image_handle));
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-13-3.png)
接收数据时候指定接收数据的端口号
  if (arg1 != nullptr) {
    HIAI_ENGINE_LOG("register input will be dealing!");
    shared_ptr<FaceRecognitionInfo> register_img = static_pointer_cast <
        FaceRecognitionInfo > (arg1);
    ret = Detection(register_img);
  }
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-13-4.png)

