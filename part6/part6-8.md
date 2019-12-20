## 6.8 将C30(Web版IDE)的工程迁移到C32(桌面版IDE)，要修改哪些部分
### 问题描述
将C30的工程迁移到C32，要修改哪些文件？
### 问题解决
1. 去掉之前工程中所有的shell脚本文件
2. 在工程中新建src目录，script目录，src目录用于存放引擎文件，main.cpp、 main.h，以及编译文件CMakeList.txt
3. 在script目录中添加deploy.sh，func_until.sh，这两个文件可以在码云源码上C32的人脸检测项目上找到。如果项目中用到ezdvpp的api，可以添加build_ezdvpp.sh
4. 修改CMakeList.txt：参考之前每个引擎下的makefile，修改默认生成的CMakeList.txt，如下图所示：
默认生成的编译文件
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part6/img/6-8-1.png)
修改CMakeList.txt的部分
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part6/img/6-8-2.png)
