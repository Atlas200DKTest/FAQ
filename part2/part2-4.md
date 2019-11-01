## 2.4 开发者板无法正常连接UI Host如何处理
### 问题描述
有以下几种现象：
  将制作好的SD卡插入开发者板并上电后，开发者板LED1与LED2灯状态信息异常。
  将制作好的SD卡插入开发者板，并通过USB方式连接UI Host，上电、开发者板启动完成后，UI Host侧无虚拟网卡信息。
  将制作好的SD卡插入开发者板，并通过NIC方式连接UI Host，上电、开发者板启动完成，配置UI Host网卡信息后，UI Host无法与开发者板通信。
### 解决思路
按照如图2-1所示流程进行排查。

![图1.1 ](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-1.jpg)
### 解决方法
#### 步骤1 确认SD卡制作正确并成功。
请查看制卡脚本所在目录下的sd_card_making_log查看是否制卡成功，若制卡失败，请参考制作SD卡重新制作SD卡。
#### 步骤2 将成功制作的SD卡插入Atlas 200 DK开发者板，并上电。
若Atlas 200 DK开发者板的LED1与LED2状态正常，即启动成功后，LDE1与LDE2同时处于亮的状态，则执行步骤3。
若Atlas 200 DK开发者板的LED1与LED2状态异常，即启动很长一段时间后（15分钟以后），LED1与LED2不同时为亮的状态，则执行步骤4。
#### 步骤3 连接Atlas 200 DK开发者板与UI Host。
若通过USB方式连接开发者板，但UI Host侧不显示虚拟USB网卡。
首先检查USB网线，确保USB网线两端口连接正常。
若UI Host侧仍然显示USB虚拟网卡，请尝试使用NIC方式连接。
若通过NIC方式连接开发者板，配置好UI Host侧的IP信息后，UI Host无法与开发者板通信。
首先检查网线，确保网线两端口正常，然后重新配置UI Host侧IP地址。
若UI Host仍然无法与开发者板通信，请尝试使用USB方式连接开发者板。
若USB方式与NIC方式，都无法正常连接UI Host与开发者板，请执行步骤步骤4。
#### 步骤4 参考通过串口连接Atlas 200 DK将Atlas 200 DK开发者板的Mini模块通过串口线与UI Host相连。
#### 步骤5 在UI Host中安装网络调试工具与USB转串口驱动软件。
网络调试工具推荐使用IPOP工具。
USB转串口驱动软件请使用PL2303驱动软件。
#### 步骤6 打开网络工程调试工具，以IPOP工具为例，进入串口窗口。
1.单击“终端工具”页签。
2.在菜单栏选择，进入“设置”窗口。
3.进行连接配置。
−连接名称：自定义连接名称。
−类型：选择COMX，可以通过计算机的设备管理器查看可用的COM端口，拔插UI Host上的串口连接线，判断Atlas 200 DK使用的哪个COM口，如图2-2所示。

![图2-2](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-2.jpg)
−设置波特率为115200。
4.单击确定。
#### 步骤 7 上电Atlas 200 DK开发者板，在IPOP的COM连接窗口中查看Atlas 200 DK启动信息。
由于启动日志较多，单击菜单栏中的将启动日志保存到IPOP工具的安装目录中，当此按钮变为，IPOP工具底部会出现文件已保存的提示信息，可以根据提示信息在IPOP安装目录中获取以当前时间命名的日志文件。
#### 步骤 8 在Ascend论坛上发求助帖，并将启动日志信息作为帖子的附件上传，将会有华为工程师为您解答。
----结束