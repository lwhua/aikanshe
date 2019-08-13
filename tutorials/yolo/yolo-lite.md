# 精简版yolo

目前目标检测神经网络都不适用于互联网应用，GPU服务器价格昂贵，因此需要一个可以在CPU服务器上运行的神经网络。

## 使用步骤
1. 下载配置文件：https://github.com/reu2018DL/YOLO-LITE/blob/master/cfg/tiny-yolov2-trial13-noBatch.cfg
2. 更改配置文件中的classes、convolutional的 filters 参数，注意：
	* yolo-lite基于yolo-v2，convolutional filters 参数设置为(classes + 5)x5
3. 其他步骤和训练yolo-v3的数据都是一样；
