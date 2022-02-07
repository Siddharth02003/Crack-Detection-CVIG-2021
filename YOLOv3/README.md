# YOLO #
YOLO (You Only Look Once) is an algorithm that uses neural networks to provide real time object detection. This model reframes object detection as a single regression problem, and uses IoU, Non-Max Supression and Anchor Boxes to effectively detect and segment objects. You can find the paper here: https://arxiv.org/abs/1804.02767

## What is YOLO? ##
You Only Look Once- Real time object detection- 45fps
Reframes object detection as a single regression problem.
So instead of having several neural networks interconnected with each other, there is just one model which does all the work- classification, localization, detection, and segmentation. 
The model has just 24 convolutional layers followed by 2 FC layers. 
The single CNN predicts bounding boxes and class probabilities for those boxes.
It divides the image into an S × S grid and for each grid cell predicts B bounding boxes, confidence for those boxes, and C class probabilities. These predictions are encoded as an S × S × (B ∗ 5 + C) tensor.



At test time, each grid cell predicts B bounding boxes and confidence scores for those boxes. These confidence scores reflect how confident the model is that the box contains an object and also how accurate it thinks the box is that it predicts.


## How to Use ##
Clone this repo and open the [YOLOv3-Crack Detection.ipynb](https://github.com/rudsamn/Crack-Detection-CVIG-2021/blob/main/YOLOv3/YOLOv3-%20Crack%20Detection.ipynb) notebook. 
1. Clone Darknet repo (You can find the repo here: https://github.com/AlexeyAB/darknet)
2. Enable OPENCV and GPU in makefile. Then run the makefile to load Darknet.
3. Ensure the dataset is in the necessary format- all the images, along with their annotations (in .txt format) should be in the same folder. 
4. Edit the yolov3_custom.cfg file as per your needs. Recommeded configs are batch = 64 and subdivisions = 16. Change the number of classes, filters and max_batches. 
5. Create obj.names with names of the classes and obj.data with locations of test, train, valid and backup folders. 
6. Generate a train.txt file which has relative paths to all files. You can find the script for the same here: [
YoloGenerateTrainingFile](https://github.com/theAIGuysCode/YoloGenerateTrainingFile/blob/master/generate_train.py/)  
7. If desired, download pre-trained weights. 
8. Train the model on the custom dataset. 

## Best Performing Checkpoints ##
The best results were obtained for the following weights: https://drive.google.com/file/d/1-HQfWD9168jvwyVt1-iaKAzKEGTGGUTq/view?usp=sharing

## Some Results ##

After training the model for 4000 epochs, the loss function we obtained is as follows:

<div align="center">
  <img width="40%" alt="Loss" src="https://github.com/rudsamn/Crack-Detection-CVIG-2021/blob/main/YOLOv3/assets/Loss.png">
</div> 

Further, the some of the results we otained are:
<div align="center">
  <img width="40%" alt="Volker_DSC01709_269_118_1281_1314.png" src="https://github.com/rudsamn/Crack-Detection-CVIG-2021/blob/main/YOLOv3/assets/Volker_DSC01709_269_118_1281_1314.png">
  <img width="40%" alt="Sylvie_Chambon_056.png" src="https://github.com/rudsamn/Crack-Detection-CVIG-2021/blob/main/YOLOv3/assets/Sylvie_Chambon_056.png">
  <img width="40%" alt="GAPS384_train_0542_1_641" src="https://github.com/rudsamn/Crack-Detection-CVIG-2021/blob/main/YOLOv3/assets/GAPS384_train_0542_1_641.png">
  <img width="40%" alt="Eugen_Muller_9360_99_556_518_594.png" src="https://github.com/rudsamn/Crack-Detection-CVIG-2021/blob/main/YOLOv3/assets/Eugen_Muller_9360_99_556_518_594.png">
  <img width="40%" alt="DeepCrack_11123" src="https://github.com/rudsamn/Crack-Detection-CVIG-2021/blob/main/YOLOv3/assets/DeepCrack_11123.png">
</div> 

## References ##
* [YOLOv3-Cloud_Tutorial](https://github.com/theAIGuysCode/YOLOv3-Cloud-Tutorial)
