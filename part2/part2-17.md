## 2.17 Brazil,制卡报错
### 问题现象
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-17-1.jfif)
### 问题分析
ubuntu版本问题，卡的大小显示中带逗号，影响了脚本判断卡的大小
### 解决方法
在文件make_sd_card.py  将第186行逗号后面加一个空格，能正常识别卡的大小即可成功

