## 4.19 Presenter Server显示文字时有重叠现象
### 问题描述
Presenter Server端展示结果时候文字重叠了如何解决？
### 解决方法
Engine后处理结果append后需要清空。
在后处理模型的CPP代码中添加如下语句：DetectionResult oneResult; 将此语句放在循环语句中即可。
