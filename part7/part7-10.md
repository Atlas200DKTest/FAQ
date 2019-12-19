## 7.10 原始YUV图片经过处理后的resized_img替换到原始图片的位置，yuv图片转换成JPEG格式失败。
### 问题描述
人脸识别示例中原始YUV格式图片可以转换成JPEG格式，经过resize预处理后的yuv图片转换成JPEG格式失败。我就是把经过处理后的resized_img替换到原始图片的位置，请问我还应该注意什么呢？


### 问题思路：
你好,经过查看代码,经过resize预处理后的yuv图片转换成JPEG格式失败的原因分析如下:
ImageData<u_int8_t> resized_img;
HIAI_StatusT vpc_ret = ImagePreProcess(image_handle->v_img.img, resized_img);
ImagePreProcess函数调用之前申请了一段内存空间,resized_img,并没有初始化这段内存空间,这段内存在ImagePreProcess函数中对其中图片的数据buffer进行了放缩,之后对这个resized_img的结构体只修改了data指针(指向放缩后的图片数据buffer),和这段空间的大小size.
  // dvpp_out->pbuf
resized_img.data.reset(dvpp_out.buffer, default_delete<uint8_t[]>());
resized_img.size = dvpp_out.size;
并没有为width和height两个结构体内的成员赋值,所以这两个成员的内容是脏的,无效数据.
所以将这个含有无效数据的resized_img的结构体赋值给描述原始图片信息的结构体image_handle时会使其中的数据成员的信息丢失成无效数据,导致在接下来数据格式转换时ConvertImage函数以image_handle为输入参数获取其中的宽高数据时会获取到无效数据,进而导致格式转换失败.
uint32_t width = img.img.width;
uint32_t height = img.img.height;
uint32_t img_size = img.img.size;

