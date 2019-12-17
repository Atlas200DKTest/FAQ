## 1.12打开mindstudio后显示无法初始化IDE是什么问题：Unable to initialize IDE
### 问题现象
![图1-12-1](https://gitee.com/Atlas200DK/FAQ/raw/master/part1/img/1-12-1.jfif)
### 解决方法
将~/tools/scripts下的env.conf里面配置的ip改下，改成127.0.0.1
然后在~/tools/bin 先执行./stop.sh 再执行./start.sh

