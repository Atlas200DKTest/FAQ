## 3.10 如何给模型的某一层赋初值
### 问题描述
原项目推理前给模型的某一层赋了一个初值，如下所示：
pts_in_hull = np.load('./resources/pts_in_hull.npy') # load cluster centers 
net.params['class8_ab'][0].data[:,:,0,0] = pts_in_hull.transpose((1,0)) # populate cluster centers as 1x1 convolution kernel
该初值从pts_in_hull.npy中读取。怎么在通过Mind Studio进行模型转换时把初值传给对应模型？
### 解决方法
由于当前Mind Studio不支持给转换好的om模型传值，所以尝试直接从转换前的模型层面上改动。
caffe的python接口可以加载模型，修改、并保存模型，于是用python直接修改并保存模型：
Python 3.7.3 (default, Mar 27 2019, 22:11:17)  
[GCC 7.3.0] :: Anaconda, Inc. on linux 
Type "help", "copyright", "credits" or "license" for more information. 
>>> import numpy as np 
>>> import os 
>>> os.environ["GLOG_minloglevel"] = '3' 
>>> import caffe 
>>> net = caffe.Net("/home/mindstudio/Desktop/colorization_deploy_v2.prototxt","/home/mindstudio/Desktop/colorization_release_v2.caffemodel",caffe.TEST) 
>>> netNew = caffe.Net("/home/mindstudio/Desktop/colorization_deploy_v2 (copy).prototxt","/home/mindstudio/Desktop/colorization_release_v2 (copy).caffemodel",caffe.TEST) 
>>> pts_in_hull = np.load('./resources/pts_in_hull.npy') 
>>> netNew.params['class8_ab'][0].data[:,:,0,0] = pts_in_hull.transpose((1,0)) 
>>> netNew.save('myCaffemodel.caffemodel') 
>>> netNew123 = caffe.Net("/home/mindstudio/Desktop/colorization_deploy_v2 (copy).prototxt","myCaffemodel.caffemodel",caffe.TEST)>>> a = netNew123.params['class8_ab'][0].data
把修改保存后的模型转换为后缀为om的离线模型，放进样例中执行，可以看到推理有结果了（推理结果不为0，之前推理结果都是0）：
[INFO][general_post.cpp 167] Success to deal file=/home/HwHiAiUser/bird.jpeg. 
[INFO][general_post.cpp 168] Top index and confidence:0:-0.503906,1:-0.150513,2:-0.236938,3:-0.117981,4:-0.138062,5:-0.060913,6:-0.156372,7:-0.181274,8:-0.272461,9:-0.343994,10:-0.530762,11:-0.324219,12:-1.128906,13:-0.887695,14:-2.269531,15:-2.376953,16:-2.974609,17:-2.291016,18:-2.404297,19:-1.718750,20:-1.685547,21:-1.215820,22:-1.280273,23:-0.916016,24:-1.057617,25:-1.271484,26:-2.189453,27:-2.482422,28:-2.486328,29:-1.641602,30:-1.862305,31:-1.225586,32:-1.142578,33:-1.186523,34:-1.792969,35:-1.837891,36:-2.171875,37:-1.637695,38:-2.203125,39:-1.584961,40:-1.832031,41:-1.393555,42:-1.651367,43:-1.212891,44:-1.730469,45:-1.314453,46:-1.701172,47:-1.130859,48:-1.541992,49:-1.052734,50:-1.531250,51:-0.952148,52:-1.141602,53:-0.997070,54:-0.748047,55:-0.554688,56:-1.011719,57:-0.343750,58:-0.135620,59:-0.133911,60:-0.085449,61:-0.102600,62:-0.028641,63:-0.058228,64:0.050537,65:-0.024734,66:-0.550781,67:-0.867188,68:-1.137695,69:-0.947754,70:-1.860352,71:-1.692383,72:-1.887695,73:-1.550781,74:-1.223633,75:-0.919922,76:-1.112305,77:-1.002930,78:-1.116211,79:-1.174805,80:-1.085938,81:-1.369141,82:-1.546875,83:-1.558594,84:-1.459961,85:-1.369141,86:-1.384766,87:-0.976562,88:-1.034180,89:-0.901855,90:-1.054688,91:-1.151367,92:-0.928223,93:-1.189453,94:-0.965332,95:-1.183594,96:-0.842773,97:-1.064453,98:-0.848633,99:-1.011719,100:-0.936523
