## 7.2  DVPP运行报不支持渐进式编码错误
### 问题现象
DVPP报错：not support progressive mode，如图4-2所示。
图4-2错误示例
![图7-2-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part7/img/7-2-1.png)

### 解决方法
DVPP硬件不支持渐进式编码，需要使用非渐进式编码的jpeg图片，渐进式jpeg可参考进行了解。https://www.jianshu.com/p/e1b9d9aa9fc0
DVPP支持的图片格式请参考《DVPP API参考》。
