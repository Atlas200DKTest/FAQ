## 2.20 快速流程编排运行Resnet18的Demo无结果，直接在开发板上运行可执行程序，报错：cannot find libteec.so.1.0
### 问题现象
在MindStudio中快速流程编排运行Resnet18的Demo，运行无结果。
### 解决方法
在MindStudio中点击run之后运行失败，无法查看结果，于是登录MindStudio，找到该Demo编译生成对的可执行文件，./workspace_mind_studio_Demo运行后报错：cannot find libteec.so.1.0，用find命令查找到对应库文件后发现，该库文件存在，但是是root属组的，没有设置其他用户的可读权限。修改库文件权限后该问题即解决

