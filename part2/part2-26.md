## 2.26 Atlas200DK单板支持jsoncpp
### 问题描述
开发板环境目前不支持jsoncpp库， jsoncpp库也没有arm版本
### 解决方法
jsoncpp库没有arm版本，需要在 arm环境下编译安装。jsoncpp是cmake编译的，在开发板上安装时，需要开发板先安装cmake，而cmake也需要编译安装，并且在开发板上编译的时候报很多错误。所以只能选择在服务器上构建交叉编译环境。步骤：

1.从github上下载jsoncpp源码

2.wget https://github.com/open-source-parsers/jsoncpp/archive/master.zip；

3.配置源码的交叉编编译环境。在我们安装了DDK的服务器上，arm的编译器在/usr/bin目录下，所以我们在jsoncpp目录下的CMakelist.txt中添加：
SET(CMAKE_SYSTEM_NAME Linux)
SET(CMAKE_C_COMPILER "/usr/bin/aarch64-linux-gnu-gcc")
SET(CMAKE_CXX_COMPILER "/usr/bin/aarch64-linux-gnu-g++")
SET(CMAKE_FIND_ROOT_PATH /usr/aarch64-linux-gnu/)
SET(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)
SET(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
SET(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)

4.在源码目录下执行下述命令，即可编译得到arm的libjsoncpp.so
cd jsoncpp-master
mkdir -p ./build/debug
cd ./build/debug
cmake -DCMAKE_BUILD_TYPE=debug -DBUILD_STATIC_LIBS=OFF -DBUILD_SHARED_LIBS=ON -DCMAKE_INSTALL_INCLUDEDIR=include/jsoncpp -DARCHIVE_INSTALL_DIR=. -G "Unix Makefiles" ../..
sudo make && make install

