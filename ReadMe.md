# INNOPOLIS DETECTOR
Before proceeding further, Feel free to take a look on the main pieces of code through this [collab notebook](https://colab.research.google.com/drive/1UeGYJcAHDQNUi_Ms1rHBRuHfDa5oHMP7?usp=sharing) 

Do you know what is so great about ***Innopolis*** City ? Well, it is not only a singly thing, but Innopolis is this ever-evolving city where humans and robots live in harmony and peace (well technically robots are saving us the trouble of leaving the comfort of our homes in the harsh Russian winter, but that's just a technicality...) 

Yet, preparing for the darker days, the days where ***MACHINES*** would rebel against the human race, I attempted to build a ***PERSON VS ROBOT*** detector to separate our allies from our enemies. The question now is ***HOW ?***
## BUILDING THE DATASET
### IMAGES
I took the responsibility of collecting enough data for my supreme goal. With the help for several friends I managed to extend my initial dataset of only 50 pictures by $3$ times ending up with a dataset of 150 pictures. (no worries, I have some data augmentation up my sleeves). Maybe we can check a couple of them: 
![image info](documents\p+r.jpg)
![image info](documents\p1.jpg)
![image info](documents\r1.jpg)
### Annotations
What about annotations now ? Well [Roboflow](https://roboflow.com/) is the best friend of Computer Vision practitioners (and humanity in general...). The latter is making the procedure quite smoother and much more efficient. Here is our data looks now: 
![](documents\annotated_1.png)

### Data Augmentation
Well as you can see in the picture above, some random noise was added to the image. That's part of the data augmentation operations I used to expand the dataset. At this initial version of the project, I decided to experiment with only two techniques:
1. Noise: between up to $3\%$
2. Exposure: between $-8\%$ and $+8\%$

### Dataset's health
Roboflow performs a health check for the dataset. Hopefully our data does not have any significant issues: 
![](documents\health.png)
Sounds pretty good to me !! let's go
# Building the Detector
## Yolov5
The first model I trained on the custom dataset is the nano-sized Yolov5. The code is commented and explained thoroughly in the accopagning notebooks, but the process can be summarized as follows:
1. installing the dependencies and importing the necessary packages
2. importing the yolob5 version of the custom dataset
3. training and evaluating the model through the scripts provided by Yolov5.

![](documents\testing.png)

The model performed quite well on the tiny dataset. Certain issues can be resolved with more data (or probably ROBOFLOW PREMIUM ACCOUNT for more augmented data). The details are also considered in the corresponding notebooks.

## Faster RCNN
The first model I trained on the custom dataset is the nano-sized Yolov5. The code is commented and explained thoroughly in the accopagning notebooks, but the process can be summarized as follows:
1. installing detectron2 and importing the necessary packages
2. importing the different functions and modules
3. downloading the dataset in the COCO format for easier registration
4. training and evaluating the model through detectron2 functionalities.

![](documents\rcnn_pred.png)

The model performed quite well in detecting the **PERSON** class. However, the performance was significantly poor for the **ROBOT** class (friendly fire!!!). More details can be found in the corresponding notebooks

## Models Comparison
YOLOV5 (the nano model) VS FASTER RCNN:
1. Mean Average Precision: 0.47 VS 0.698
2. Inference time: 192 ms VS 6.6 ms
3. Memory Requirements: 28.5 MB VS 6.7 GB

Even though Faster RCNN outperforms Yolov5 in Mean Average Precision, The boost in performance introduced by Faster RCNN might not be proportional to memory requirements and inference speed especially with Yolov5 (the nano model) is quite likely to be improved with a larger training dataset and more data augmentation techniques. 

# Conclusion
Our small detector was done in Innopolis, from Innopolis to Innopolis. Our small detector here is quite promising. Nevertheless, it is not ready for our futuristic supreme goal. Any feedback, ideas for improvements would be greatly appreciated. 