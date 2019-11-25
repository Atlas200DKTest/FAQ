## 7.3 cv:imread与pil的open image格式的差别
### 问题描述
cv:imread 和pil open image读出来的图片格式一样吗？

### 问题解决
PIL.Image.open()函数读取的图片格式要求为RGB, PIL.Image.save()直接保存RGB格式的图片。
cv2.imread()函数读取的图片格式要求为BGR。
如果推理需要输入的图片格式为BGR，则使用cv2.imread()读取出的图片可以直接使用，使用PIL.Image.open()读取出的图片需要转换成BGR格式后使用。
