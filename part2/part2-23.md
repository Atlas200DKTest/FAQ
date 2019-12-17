## 2.23 Host和Device可以交叉运行么？
### 问题描述
是否支持host-device-host-device-host（分别对应拉流-解码推理-后处理-编码h264-推流），还是host侧只能在首尾，也就是拉流和推流。其余处理都要放在device侧？
### 解决方法
只要没有使用到Device侧的库和文件等（比如HIAI相关），就可以在host侧运行。Engine之间是通过senddata进行消息的串联，和在Device还是Host侧没有必要的关系。在中间这一步的后处理只要在graph.config中定义了在host侧运行，并且没有使用到Device侧的相关库和文件，就可以接收上一个Device侧的Engine的消息，并在处理完成后发送到下一个Device侧的Engine中

