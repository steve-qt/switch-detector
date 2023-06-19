## switch-detector

This project is to detect whether cables are plugged into switch or not using yolov5.
It includes two main parts:

--------Training prediction model on google colab with GPU--------
(or download the weight from https://drive.google.com/file/d/1z9ZDBfH0jZ788XttENy271ZfH2Ccq5ZO/view?usp=sharing)

+ Prepare the dataset on roboflow (assign, annotate and augment)
	https://app.roboflow.com/steven-luong-gp8uk/switch-detector/4

+ Training model on google colab:
	https://colab.research.google.com/drive/16o7OXcuMQxIjHY0FHYYOA8VPKJ4WXmxX?usp=sharing

+ Download and save the weight(in this case, it's the "best.pt")

---------------Converting from yolov5 to openvino (optional)-----

 		
		py export.py --weights .\best.pt --include torchscript onnx


---------------------Detecting on local--------------------------
+ Run the detector with your choice of weight (either .pt or .onnx)

	with video "switch-sample.mov": 
	
		python detect.py --agnostic --weights best.pt --img 640 --source switch-sample.mov --conf 0.5 --iou 0.65

	with rstp:
		
		python detect.py --agnostic --weights best.pt --img 640 --source <rtsp-link> --conf 0.5 --iou 0.65

