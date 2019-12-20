## 4.38 face-detection-sample-python的Process入口是如何被使用的
### 问题描述
想问一下在face-detection-sample-python的main.py的74行
faceDetectGraph.StartupEngines(engineList)
StartupEngines()方法中调用EngineThread.start()方法，但是

class EngineThread(threading.Thread):
def __init__(self, engineObj):
threading.Thread.__init__(self)
self.engine = engineObj
self.msgQueue = engineObj.msgQueue

def run(self):
print(self.name,"start...")
while True:
dataType = self.msgQueue.msgQueue.get()
msgData = self.msgQueue.dataQueue.get()
if msgData == None:
print("Message ", dataType, " data is None!")
continue
self.engine.Process(msgData)
print(self.name, "finished")
class EngineThread却没有start方法，是怎么回事呢？
### 解决方法
EngineThread继承自Thread线程类，这是启动线程start方法，是父类里面的方法，run方法是重写父类Thread类的run方法

