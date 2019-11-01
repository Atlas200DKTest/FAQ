## 6.3 如何离线部署MindSpore Studio或者Atlas 200 DK依赖软件
### 背景
若MindSpore Studio所在Ubuntu服务器无法连接网络，则无法直接在线安装MindSpore Studio或者Atlas 200 DK交叉编译环境依赖软件，例如：gcc g++ cmake curl libboost-all-dev libatlas-base-dev unzip haveged liblmdb-dev  qemu-user-static binfmt-support python3-yaml gcc-aarch64-linux-gnu g++-aarch64-linux-gnu等，详细依赖可以参考《Ascend 310 MindSpore Studio工具安装指南（Ubuntu，X86）》与《Ascend 310 Atlas 200 Developer Kit 使用指导》，此时需要离线部署这些依赖软件。
### 操作步骤
#### 步骤 1
    在一台可以连接网络的Ubuntu 16.04.3的服务器中，参考《Ascend 310 MindSpore Studio工具安装指南（Ubuntu，X86）》与《Ascend 310 Atlas 200 Developer Kit 使用指导》在线安装依赖软件。
例如：执行apt-get install gcc-aarch64-linux-gnu命令安装交叉编译器。
依赖软件在线下载完毕后，可以在当前连接网络的Ubuntu服务器的“/var/cache/apt/archives”路径下获取已下载的依赖软件的.deb包。
#### 步骤 2
    将步骤1中获取的.deb包以MindSpore Studio安装用户上传到MindSpore Studio所在的Ubuntu服务器任一目录。
#### 步骤 3
    执行如下命令安装.deb包。
sudo dpkg -i deb软件包名
##### 说明
若安装过程中需要部署依赖包，请参考步骤1~步骤3先在MindSpore Studio所在Ubuntu服务器中部署依赖包，再重新执行此包的安装。
----结束

