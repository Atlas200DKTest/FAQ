## 5.9 1.3.0.0文档中关于AI Core metrics相关说明的疑问
### 问题描述
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part5/img/5-9-1.png)
对应的文档链接为https://ascend.huawei.com/doc/Atlas%20200%20DK/1.3.0.0/zh/zh-cn_topic_0160785653.html
可以看出，0x4a和0x49在首段被描述为“cube指令数”；但在mac_fp16_ratio和mac_int8_ratio的计算中虽然使用了所谓“指令数”事件，但描述却为“cube指令的cycle数”占比。两处的描述存在矛盾。
1、0x4a和0x49究竟是指令数还是cycle数？
2、mac_fp16_ratio和mac_int8_ratio与total_time乘积，是否为实际运算的时间？
在AI Core Metrics性能采样结果中，还有一个"mac_ratio" (对应事件0x3)，按照文档中说明，该数据表明”cube类型指令（未包含特殊寄存器写请求）的cycle数在所有指令的cycle数中的占用比“。
3、请问这个mac_ratio和mac_fp16_ratio以及mac_int8_ratio是什么关系？为什么profile结果中mac_ratio的值相比mac_fp16_ratio（或者mac_int8_ratio)小很多？
4、mac_fp16_ratio + vec_ratio + scalar_ratio的结果会大于1吗？我的Profile数据中发现他们的和会出现大于1的情况，如何解释呢？是否表示mac_fp16操作、vector操作和scalar的操作有重叠？数据搬移（或者DMA 操作）的ratio包含在scalar ratio里面吗？
5、关于iq_full_ratio的百分比是什么含义？比如mte0_iq_full_ratio、mte1_iq_full_ratio、mte2_iq_full_ratio怎么理解？


### 解决方法
1. 0x4a事件表示的是cube int类型指令执行的cycle数，0x49表示的是cube FP类型指令执行的cycle数
    mac_fp16_ratio代表cube fp类型指令的cycle数占比
    mac_int8_ratio代表cube int类型指令的cycle数占比
2. mac_fp16_ratio和mac_int8_ratio与total_time乘积结果为相应指令执行的时间
3. 当前所提供的mac_ratio计算公式计算的是0x3/task_cycle,其中0x3事件采集的是cube类型指令数。
mac_int8_ratio以及mac_fp16_ratio指标计算的是cube int类型以及cube fp类型指令执行cycle数占比。
两者无直接关系
更正资料，0x3采集的是cube类型指令数，0x8表示vector指令执行的cycle数，0x9表示scalar指令执行的cycle数，0xe表示总指令cycle数，0x3a表示scalar访问UB读请求类型指令执行的cycle数，0x3b表示scalar访问UB写请求类型指令执行的cycle数。0x4a表示cube int类型指令执行的cycle数，0x49表示cube FP类型执行执行的cycle数
4. D芯片是多发射系统。如果完全并行起来，那其实可以到3.0 i.e. 100% vec 在忙, 100% scalar 在忙 , 100% cube 在忙
5. scalar pipeline因为MTE的命令反应，使得scalar pipeline跑不下去的比例

