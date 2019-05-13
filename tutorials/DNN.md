#神经网络


##样例：

```
	Net net = Dnn.readNetFromDarknet(cfgFile, weights);

	Size sz = new Size(416,416);

	float scale = 1.0F / 255.0F;
	Mat inputBlob = Dnn.blobFromImage(frame, scale, sz, new Scalar(0), false, false);   //Convert Mat to batch of images
	net.setInput(inputBlob);

	List<Mat> outs = new ArrayList<Mat>();
	List<String> outNames = net.getUnconnectedOutLayersNames();
	net.forward(outs,outNames);
	MatOfInt outLayers = net.getUnconnectedOutLayers();
	int[] layer = new int[1];
	outLayers.get(0,0,layer);
	int layerid = layer[0];
	String outLayerType = net.getLayer(new DictValue(layerid)).get_type();

	List<double[]> coatingpointColor = new ArrayList<double[]>();
	Rect rect = new Rect();

	if(outLayerType.equals("Region")){
		for (int i = 0; i < outs.size(); i++) {
			Mat detectionMat = outs.get(i);
				for (int r = 0; r < detectionMat.rows(); r++)
				{
					int probability_index = 5;
					int size = (int) (detectionMat.cols() * detectionMat.channels());

					float[] data = new float[size];
					detectionMat.get(r, 0, data);

					float confidence = -1;
					for (int j=0; j < detectionMat.cols();j++)
					{
						if (j >= probability_index && confidence < data[j] )
						{
							confidence = data[j];
						}
					}
					System.out.println("confidence: " + confidence);
					
				}
		}
	}
```