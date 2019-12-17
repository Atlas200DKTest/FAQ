## 1.15 如何离线安装Mind Studio的安装依赖？
### 问题现象
怎么从一台联网的PC机上打包Mind Studio的依赖环境到另一台不联网的PC机上去安装？

### 问题解决
1.apt-get命令安装的包
apt-get install命令会在默认的路径下下载deb的包，这个路径是/var/cache/apt/archives因此我们只需要打包这里的deb安装包就可以了，这里包比较多，我们打包archives这个文件夹会方便一点；
把上述对应的包拷贝到另一台PC机上，对于archives这个文件夹，解压后，使用命令
sudo dpkg -i *.deb即可安装
2.对于pip安装的包
由于源码安装需要的时间过长，我们则可以去python的官网去下载对应的.whl包即可。对于whl的包，python2使用
pip2 install xxxxx.whl
对于python3使用
pip3 install xxx.whl

