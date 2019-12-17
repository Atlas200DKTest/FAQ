## 2.22 开发板上python3里安装opencv
1.下载源码
git clone https://github.com/opencv/opencv.git
git clone https://github.com/opencv/opencv_contrib.git
2.安装构建opencv的工具：
apt-get install build-essential -y
apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev libv4l-dev -y
3.在opencv中构建环境
cd opencv
mkdir release
cd release/
cmake -D BUILD_opencv_python3=YES -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_LIBV4L=ON -D OPENCV_EXTRA_MODULES=../../opencv_contrib/modules -D PYTHON3_LIBRARIES=/usr/lib/arm-linux-gnueabihf/libpython3.5m.so -D PYTHON3_NUMPY_INCLUDE_DIRS=/usr/local/lib/python3.5/dist-packages/numpy/core/include/ ..
4.编译
make -j8
5.安装并更新动态库
make install
ldconfig

至此，opencv已编译安装完成，可以在python3中import cv2进行验证。
![img](https://gitee.com/Atlas200DK/FAQ/raw/master/part2/img/2-22-1.png)

