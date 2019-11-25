## 7.6 VPC resize时宽高同时放大或者缩小的操作是否可一次性完成
### 问题描述
开发者在处理图片的时候，如果需要同时放大或者缩小宽和高，可以通过VPC的resize功能一次性完成吗？

### 解决方法
VPC图片的缩放比例如果在宽[1/32,16] 、高[1/32,16] 的范围内，则可以一次性的resize，即宽与高可以缩小为1/32倍，高放大16倍。
针对C10版本VPC老接口，有如下宽和高缩放范围的限制。
![图7-6-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-6-1.png)
如果不在此范围内，则建议升级到C30版本，若无法做版本升级可以先做宽缩放，高不变，再做高的缩放，宽不变。
例如宽缩放比例在[1/8,2],高缩放比例在[2,4]，则一次完成不了。
如下报错信息，针对C10 VPC老接口，高放大[1/4,4]，宽缩小[1/8,2]，则会报错。
[SetScalerInfoBranch:105] [L20] scaler fail. because hinc = outWidth(128)/cropWidth(44) =2.909091. vinc = outHeight(112)/cropHeight(524) = 0.213740. hinc and vinc must be in [0.03125,16]
