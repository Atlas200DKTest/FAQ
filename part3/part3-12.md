## 3.12 omg转模型时操作libfmk_common.so 找不到
### 问题描述
使用omg转模型的时候报错找不到libfmk_common.so

### 解决方法
按照https://ascend.huawei.com/doc/Atlas200DK/1.3.0.0/zh/zh-cn_topic_0165968579.html 的说明设置环境变量 ：
export  LD_LIBRARY_PATH=DDK安装目录/ddk/uihost/lib


