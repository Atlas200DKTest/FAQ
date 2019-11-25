## 7.1  执行DVPP的VPC功能时报ioctl fail错误定位方法
### 问题现象
ioctl是DVPP调用硬件的处理接口，ioctl出错也是VPC最常见的错误，错误原因大概可以分为如下四大类：
图4-1VPC出现ioctl fail错误常见原因
![图7-1-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-1-1.png)
输入或输出内存不是4G空间
错误示例
输入和输出都不是4G空间内存的打印示例如下（CMDLIST接口打印）。
![图7-1-2](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-1-2.png)
输入不是4G空间内存，输出是4G空间内存的错误打印。
![图7-1-3](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-1-3.png)
###  解决方法
DVPP要求同一次任务的缓冲区的输入和输出区的虚拟地址应该在同一4G空间，昇腾310提供的4G内存虚拟地址为0xffff00000000~0xffffffffffff。
可以用HIAI_DVPP_DMalloc接口申请内存，并满足对应的宽高要求（C10版本为128*16，C30版本为16*2），可以确保输入与输出在同一4G内存空间。
正确的内存打印日志以0xffff开头，输入内存打印关键词“bare_buffer”, 输出内存打印关键词“outputConfigure:addr”或者“YUV_SUM_OUT_CONFIG:out_buffer” 。
如下图所示为正确的4G空间内存打印。
![图7-1-4](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-1-4.png)
输出参数不满足VPC要求
《DVPP API参考》对VPC输入和输出内存的限制有明确的约束，代码示例也比较清晰，请参考API参考检查各字段是否正确。
不同的子功能，例如解压缩，抠图，缩放 接口的输入参数要求不一致，请严格按照《DVPP API参考》要求配置，并参考文档中的代码示例进行编程。
若自己设计的代码报错，请运行DDK中的DVPP样例代码，排查开发环境是否有问题，另外请参考DVPP样例代码排查代码设计。
VPC功能多次错误，触发硬件保护机制
若出现如下日志：
![图7-1-5](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-1-5.png)
出现关键词“p_engine_para->fail_count< (15)”，这种情况下即使接口调用正确也无法正确调用VPC接口，原因是前期调试多次输入参数或地址异常，触发硬件保护机制，这时需要重启系统。 正常业务运行不会出现情况。
注意：如果是整体业务测试性能，最好是重启系统后再进行测试，防止保护机制隔离了部分组件（共4个VPC），如果<=3个VPC隔离，业务还是可以正常运行，不会出现如上错误，但是运行性能达不到最大化。如果是16路解码，VPC解压缩就可能因为前期的调试导致后期业务测试达不到最大性能。

