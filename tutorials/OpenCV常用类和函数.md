# OpenCV常用类和函数

## 读写图片
```
	读取指定文件路径内容：Imgcodecs.imread(filePath);
	读取MultipartFile文件内容：Imgcodecs.imdecode(new MatOfByte(file.getBytes()), Imgcodecs.IMREAD_UNCHANGED);
	保存图片：Imgcodecs.imwrite(filename, image);

	读取视频：
	// 打开摄像头或者视频文件
    VideoCapture capture = new VideoCapture();
    //capture.open(0);
    capture.open("D:/vcprojects/images/768x576.avi");
    Mat frame = new Mat();
    while(true) {
    	boolean have = capture.read(frame);
    	...
    }

    显示图片：
    HighGui.imshow("H",frame);
    HighGui.waitKey(0);

```
## 颜色空间转换
```
    Imgproc.cvtColor(srcImg,image,Imgproc.COLOR_BGR2HSV);
```

## 直方图
```
	Imgproc.calcHist(mv2, channels, new Mat(), histImg, histSize,ranges);
```

## 求解矩阵最小二乘解
```
	Core.solve(X, Y, A, Core.DECOMP_LU);
```

## 阈值化
```
	Imgproc.adaptiveThreshold(image,image,255,Imgproc.ADAPTIVE_THRESH_GAUSSIAN_C,Imgproc.THRESH_BINARY_INV,25,10);

```

## 画矩形，圆形
```
	Imgproc.rectangle(frame, rect,new Scalar(0, 255, 0),1);
	Imgproc.circle(frame,point,2,new Scalar(255,0,0),2);
```

## 计算均值
```
	Scalar scalar = Core.mean(imgDesc);
```

## 截取ROI
```
	imgROI.copyTo(imgDesc);
```

## 获取某个像素点的颜色值（rgb空间）
```
	double[] midPrgb0 = frame.get(y,x);
```


## 查找轮廓
```
	Imgproc.findContours(result, contours, hierarchy, Imgproc.RETR_EXTERNAL, Imgproc.CHAIN_APPROX_SIMPLE);

```


## 图割操作
```
	//实现图割操作 结果是一个二值图像
	Imgproc.grabCut(frame, result, rect, bgMat, fgMat, i, Imgproc.GC_INIT_WITH_RECT);

```

## 神经网络【yolo】
```
	Net net = Dnn.readNetFromDarknet(cfgFile, weights);

	Mat inputBlob = Dnn.blobFromImage(frame, scale, sz, new Scalar(0), false, false);   //Convert Mat to batch of images
	net.setInput(inputBlob);

	List<String> outNames = net.getUnconnectedOutLayersNames();
	net.forward(outs,outNames);
	MatOfInt outLayers = net.getUnconnectedOutLayers();

	String outLayerType = net.getLayer(new DictValue(layerid)).get_type();
	Mat detectionMat = outs.get(i);

```
