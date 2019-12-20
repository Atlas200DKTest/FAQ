## 4.25 客户需要在小猪佩奇样例中存盘图片
### 问题描述
客户希望可以在样例流程中保存推理的图片
### 解决方法
可以在后处理引擎中将图片数据写二进制文件。代码如下：
void WriteImage(unsigned char* data, int32_t size， const char* filename)
{
	std::ofstream f(filename, std::ios::binary);
	if (!f)
	{
		 HIAI_ENGINE_LOG(HIAI_ENGINE_RUN_ARGS_NOT_RIGHT,"create file failed");
		return;
	}

	f.write((char *)data, size); 
	f.close();

