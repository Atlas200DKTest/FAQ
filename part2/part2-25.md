## 2.25 如何在单板上使用gdb查看异常
### 问题描述
样例运行时发生断异常segment fault，需要定位具体原因
### 解决方法
1.配置开发板联网；

2.在开发板上执行 apt-get install gdb安装gdb 工具；

3.开发板上输入命令ulimit -c unlimited打开coredump;

4.开发板上手动执行发生异常的样例程序bin文件，例如在/home/HwHiAiUser/HIAI_PROJECTS/ascend_workspace/objectdetection/out目录下执行 ./ascend_objectdetection
再次发生异常的时候会生成一个名为core文件

5.执行 gdb ascend_objectdetection core打开core文件；

6.执行 bt命令即可查看异常时的调用栈，然后根据调用栈分析代码找到引起异常的原因。

