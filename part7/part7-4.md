## 7.4 DVPP的VDEC为什么有HFBC的中间格式
### 问题现象
VDEC（视频解码）输出HFBC（Hisi Frame Buffer Compress）数据，即压缩格式的数据，目的是为了降低写内存的带宽。而解压缩HFBC格式数据是VPC模块的功能，因为是两个独立的模块，所以中间产生了HFBC格式的中间数据。
### 解决方法
HBFC如何发挥优势
如下图所示：
![图7-4-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-4-1.png)
用户从VDEC获取到HFBC格式的数据后，可以通过调用VPC做resize/crop操作，得到想要的输出数据，例如从VDEC获取到1920x1080的HFBC数据，然后调用VPC的resize/crop操作获得224x224的YUV数据。其中resize/crop操作可以根据用户配置参数对HFBC数据进行操作，比较灵活，而且只需要进行一次VPC，性能高（图xx中的虚线部分）。
如果用户需要使用原图，那就发挥不了HBFC的优势，但也不影响用户的业务功能。
