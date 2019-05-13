#截取ROI

样例：
```
	Rect roi = new Rect();
	//设置ROI
	Mat imgROI = new Mat(frame, roi);
	//目标Mat
	Mat imgDesc = new Mat(5, 5, CvType.CV_8UC3);
	//从ROI中剪切图片
	imgROI.copyTo(imgDesc);
```