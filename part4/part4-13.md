## 4.13 Engine实现代码中的InputSize是什么
### 问题描述
每个Engine的C++代码中都有如下宏定义：
HIAI_IMPL_ENGINE_PROCESS("face_register", FaceRegister, INPUT_SIZE)
INPUT_SIZE是什么含义？
### 解决方法
Engine.h中定义如下：
/** 
* @marco：HIAI_IMPL_ENGINE_PROCESS 
* @brief 预编译接口[注册Engine类消息处理]：放到用户自定义Engine的类实现中 
* @param [in]name:用户定义Engine的名称字符串 
* @param [in]engineClass:用户定义Engine的类名 
* @param [in]inPortNumInput:该Engine的输入端口数量 
*/ 
 #define HIAI_IMPL_ENGINE_PROCESS(name, engineClass, inPortNumInput) \ 
HIAI_REGISTER_ENGINE_UNIQUE(name, engineClass, __COUNTER__)         \ 
HIAI_StatusT engineClass::Process(HIAI_INPUT_ARGS(inPortNumInput))
INPUT_SIZE是输入端口数量。
如下图所示：
![4-13-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part4/img/4-13-1.jpg)
MindInferenceEngine_1的INPUTSIZE为3。
FasterRCNNPostProcess_1的INPUTSIZE为1。
