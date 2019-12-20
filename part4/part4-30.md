## 4.30 C31版本分类以及目标检测的sample，在开发板侧运行python脚本出错，报错：找不到可执行文件
### 问题描述
在C31版本的分类样例和目标检测样例的迁移过程中，在开发板执行python脚本时报错，报错：找不到可执行文件。
### 解决方法
经过C31 的mindstudio编译生成的可执行程序的名字有固定的命名格式：workspace_mind_studio+工程名。
因此需要写一段程序，在可执行程序的同级目录，根据上述命名规则去遍历文件查找。
添加代码如下：
def Init_CPP_EXE():
    check_flag = True
    global CPP_EXE
    file_dir=os.getcwd()
    count=0
    for dirpath, dirname, filename in os.walk(file_dir):
        if count >= 1:
            break
        for i in filename:
            if re.match("workspace_mind_studio",i):
                CPP_EXE='./'+i
                break
    if not CPP_EXE:
        eprint('[ERROR] excute file does not exist.')
        check_flag = False
    return check_flag

