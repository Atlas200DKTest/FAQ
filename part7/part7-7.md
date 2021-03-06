## 7.7 如何定位视频解码出错在哪个环节
### 解决思路
视频解码的整个过程分三个阶段， 视频流获取，数据传输， DVPP解码。 这三个过程任意一个环境出现问题都可能有解码问题，建议按照如下思路进行定位：
1. 请使用1.1.T22.B883， 1.3.T25.B883版本以上的环境（修复了一些bug）。
2. 视频流获取阶段，将数据保存下来，第三方工具（eseye_u.exe）查看是否可以正常播放。
3. 数据传输阶段， 把 Host侧准备发送给Device侧的数据写入文件，使用第三方工具（eseye_u.exe）查看是否可以正常播放。 来界定是否网络传输的问题。
4. 如果1~3未解决问题，怀疑DVPP解码有问题，可以参考发布的DDK样例中的解码代码，排查解码代码是否有问题。
5. 如果1~4还未解决问题，可以把第三步保留的码流数据用DDK中DVPP的sample进行解码验证。
