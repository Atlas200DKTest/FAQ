## 2.2 SD卡制作过程中人为拔卡导致系统存在冗余挂载盘
SD卡制作过程中人为拔卡导致系统出现冗余临时挂载盘，可使用如下步骤卸除。
### 步骤1 
    使用MindSpore Studio安装用户登录MindSpore Studio所在Ubuntu系统，并执行su - root命令切换到root用户。
### 步骤2
    输入命令df -h，查看到/dev/loop0临时挂载盘。
root@kickseed:~# df -h 
Filesystem       Size     Used      Avail   Use% Mounted on 
/dev/loop0      745M  745M     0        100% /home/ubuntu/studio/scripts/180919002200 
/dev/sdc1        118G   60M       112G  1%    /home/ubuntu/studio/scripts/sd_mount_dir
### 步骤3
    使用umount命令卸除挂载盘，命令中的/dev/loop0、/dev/sdc1设备请用户根据步骤2实际查询结果调整。
root@kickseed:~# umount /dev/loop0 
root@kickseed:~# umount /dev/sdc1
若命令提示target is busy，请尝试重启Ubuntu PC机，再重新步骤1至步骤3。
----结束
