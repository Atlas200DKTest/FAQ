## 5.15 tensorflow下ROIAlign算子怎么用
### 问题描述
tensorflow下的这个功能一般都是用crop_and_resize和avg_pool实现的。
但好像有提供一个融合的ROIAlign算子，想问一下tf的pb算子要怎么构造才能用omg转换成ROIAlign

### 解决方法
如果要构造才能用omg转换成ROIAlign的话需要自己开发tensorflow自定义算子

