# 训练样本数据

DNN网络采用yolo-v3，和v2版本相比，增加了网络的层级，支持检测小目标。

## 训练步骤

1. 收集目标图片，可以从百度图片下载，建议使用爬虫，PHP语言推荐使用php-spider，Python语言有很多开源爬虫框架；
2. 安装Yolo_mark，github地址：https://github.com/AlexeyAB/Yolo_mark ，上面介绍的比较详细，需要注意以下几点：
	* 只支持OpenCV 2.x and OpenCV 3.x，OpenCV安装参考之前的教程；
	* 编译完成后，运行x64/Release/yolo_mark.cmd，如果提示缺失opencv_ffmpeg3xx_64.dll，复制OpenCV 安装目录下的opencv_ffmpeg3xx_64.dll，到yolo_mark.cmd同级目录下

3. 标注图片，参考教程：https://blog.csdn.net/qq_33485434/article/details/80597381 ；
4. 训练网络：复制x64/Release/data目录下的所有文件到darknet安装目录对应的data目录下，更改cfg/yolov3.cfg中的classes参数，和对应的卷积层参数，具体参考：https://github.com/AlexeyAB/darknet#how-to-train-to-detect-your-custom-objects
5. 常用命令：
	* 训练命令：darknet.exe detector train data/obj.data cfg/yolov3.cfg /backup/yolov3.weights -map
	如果没有权重文件，可以省略，会随机生成一个权重文件。
	* 测试命令：darknet.exe detector test data/obj.data cfg/yolov3.cfg yolov3_final.weights,yolov3_final.weights为结束训练后的权重文件
	




