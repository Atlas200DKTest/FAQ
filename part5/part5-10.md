## 5.10 多路流的实现
### 问题描述
官方提供的实现多路流的推理例子是开启两个线程实现，如果需要实现较多路数时，比如10路输入，应该如何处理？
采用并行方式指的是拉流启用的引擎是10个，再输入到一个推理引擎中吗？

### 解决方法
多路流需要起多个线程，是在同一个引擎里面做的，按照videocar这个sample中的video_decode这个cpp文件的方式做多线程处理。并行方式处理指的是多路输入的情况下，在执行run脚本时可以填入多个输入源运行，每个输入会单独拉起线程进行解码并处理，最终每个输入都会在单独的线程中输出结果并展示到presentserver上。这个过程是并行的。
