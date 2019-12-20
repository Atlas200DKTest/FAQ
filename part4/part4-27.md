## 4.27 sample-objectdetection的图像缩放函数自动将缩放后的图片对齐
### 问题描述
sample-objectdetection的GeneralInference::PreProcess接口中，设置了is_input_align为false。无论该对齐项设置为什么值，输出的图像都是128*16对齐的。
### 解决方法
ezdvpp的参数中对齐选项有两个，一个是is_input_align，一个是is_output_align。其中is_input_align默认为false， is_output_align默认为true。前者是设置原始图像数据在缩放过程中拷贝的时候，从原始图像中拷贝实际宽度的一行数据，到目的缓存中对齐宽度的一行中。这些都是在真正缩放前进行的。 is_output_align是控制缩放后的图像是否对齐。

