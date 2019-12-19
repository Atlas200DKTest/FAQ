## 5.5 开发板在ROOT用户下用chmod修改/dev/i2c-1文件权限后，程序中可以访问控制I2C-1，但是开发板断电重启后，权限又恢复成HwHiAiUser用户无法访问。
### 问题描述
用chmod修改 /dev/i2c-1文件权限后，程序中可以访问控制I2C-1，但是开发板断电重启后，程序又不能访问/dev/i2c-1。
### 解决方法
检查后发现，断电重启后，/dev/i2c-1文件权限恢复成初始状态，查看/dev/i2c-1文件访问权限，ll /dev/i2c-1 只有ROOT和 i2c组可以访问，在控制台下，用 sudo
usermod -aG i2c HwHiAiUser，让HwHiAiUser可以永久访问I2C-1文件。
