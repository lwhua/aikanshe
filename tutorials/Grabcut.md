#图割操作

分离指定区域的前景和背景图片

##样例：
```
	Rect rect = new Rect(point1,point2);
	Mat frame = Imgcodecs.imread("2.jpg");
	//Grabcut分割前景与背景
	Mat fgMat = new Mat(), bgMat = new Mat();//定义前景与背景
	//定义迭代次数
	int i = 5;
	Mat result = new Mat(rect.size(),CvType.CV_8U);
	//实现图割操作 结果是一个二值图像
	Imgproc.grabCut(frame, result, rect, bgMat, fgMat, i, Imgproc.GC_INIT_WITH_RECT);

	//图像匹配
	Core.compare(result, new Scalar(3), result, Core.CMP_EQ);//比较result的值可能是前景才输出到result中
```