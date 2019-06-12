# 安装DarkNet

本教程安装的不是官网的darknet，而是分支：https://github.com/AlexeyAB/darknet.git
本教程显卡支持CUDA，如果显卡不支持CUDA，需要做点小修改，参考：https://github.com/AlexeyAB/darknet#how-to-compile-on-windows-legacy-way

##安装步骤

1. 安装MSVS2015
2. 下载OpenCV 3.x windows安装包，官网有下载，下载完后解压到指定目录，如：e:\opencv；
3. 安装 CUDA 10.0:https://developer.nvidia.com/cuda-toolkit-archive
4. 安装 cuDNN 7.4.1：https://developer.nvidia.com/rdp/cudnn-archive 

5. 导出项目，用vs打开 darknet.sln，设置编译环境为：x64 and Release，
	更改工程中的OpenCV的路径为本机安装路径：
	* 右击项目 =》属性 =》 C/C++ =》通用 =》附加目录 =》 添加一行： e:\opencv\opencv\build\include
	* 右击项目 =》属性 =》 链接器 =》通用 =》附加目录 =》 添加一行： e:\opencv\opencv\build\x64\vc14\lib
	* 然后右击项目 =》 生成即可生成 darknet.exe
6. 复制OpenCV 安装目录下的，opencv_world3xx.dll，opencv_ffmpeg3xx_64.dll，到darknet.exe同级目录下

##注意事项

1. 编写此文档的时候还不支持OpenCV 4.x，如果最新版已经，建议安装OpenCV 4.x
2. 建议在支持 CUDA 的电脑上安装，否则即使一个很小的神经网络，训练会非常慢

