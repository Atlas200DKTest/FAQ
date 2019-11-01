## 6.4 如何在Atlas 200 DK上运行交叉编译的OpenCV库
	在UI Host上用cmake编译出的ARM版的.so共享库，需要复制到Atlas 200 DK开发者板上的/usr/local/lib目录下，然后修改Atlas 200 DK应用程序中的ldconfig文件即可。
