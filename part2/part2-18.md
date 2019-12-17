## 2.18 Mind Studio自定义工程样例hiaiengine编译运行都正常，但是没有matrix_dvpp_framework_test_result文件生成？
### 问题描述
安装官网的教程https://ascend.huawei.com/doc/Atlas200DK/1.3.0.0/zh/zh-cn_topic_0171438081.html 指导进行工程的创建编译运行，执行后没有结果文件生成
### 解决方法
由于这个工程跑的代码是来自本地ddk里的sample样例，因此代码包含着对Atlas 200 DK形态和ASIC形态的板子，所以在阅读指导书的时候需要注意把相关的地方修改成对应的形态。
特别需要注意的是main.cpp中内存分配这里对于Atlas 200 DK要这样修改
HIAI_StatusT getRet = hiai::HIAIMemory::HIAI_DMalloc(size, (void*&)buffer, 10000,hiai::HIAI_MEMORY_ATTR_MANUAL_FREE); //Atlas 200 DK场景下，请使用HIAI_DVPP_DMalloc申请内存，即HIAI_StatusT getRet = hiai::HIAIMemory::HIAI_DVPP_DMalloc(size, (void*&)buffer）;

