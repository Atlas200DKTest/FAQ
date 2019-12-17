## 1.13 mindstudio升级IDE版本后，运行protoc找不到库protoc.so.18
### 问题现象
升级后需要对当前样例中使用的proto文件重新生成对应的cc文件和h头文件，运行新版本的protoc时报错找不到protoc.so.18
### 解决方法
新版本升级libprotobuf.so.15到libprotobuf.so.18，protoc也从3.5升级到3.7,。以前C30版本时样例中 proto文件生成的cc文件和h文件在运行的时候会报错不支持老版本。这样就需要重新用3.7版本的protoc转换proto文件。该执行文件路径为$HOME/.mindstudio/huawei/ddk/1.31.T13.B130/ddk/bin/x86_64-linux-gcc5.4/protoc， protoc.so.18的路径为 $HOME/.mindstudio/huawei/ddk/1.31.T13.B130/ddk/lib/x86_64-linux-gcc5.4/，需要设置export LD_LIBRARY_PATH=$HOME/.mindstudio/huawei/ddk/1.31.T13.B130/ddk/lib/x86_64-linux-gcc5.4

