## switch-detector

This project is to detect whether cables are plugged into switch or not using yolov5.
It includes two main parts:

(1) Training prediction model on google colab with GPU

(2) Switch Detecting on local 


--------Training prediction model on google colab with GPU--------

+ Prepare the dataset on roboflow (assign, annotate and augment)
	https://app.roboflow.com/steven-luong-gp8uk/switch-detector/4

+ Training model on google colab:
	https://colab.research.google.com/drive/16o7OXcuMQxIjHY0FHYYOA8VPKJ4WXmxX?usp=sharing

+ Download and save the weight(in this case, it's the "best.pt")


--------Switch Detecting on local---------------------

+ Clone yolov5 from git:
	git clone https://github.com/ultralytics/yolov5  # clone
	cd yolov5
	pip install -r requirements.txt  # install

+ Copy the best.pt to yolov5 directory

+ Run the detector

with video "switch-sample.mov": 
	python detect.py --agnostic --weights best.pt --img 416 --source switch-sample.mov --conf 0.5 --iou 0.65

with rstp:
	python detect.py --agnostic --weights best.pt --img 416 --source <rtsp-link> --conf 0.5 --iou 0.65

