# INNOPOLIS DETECTOR
Before proceeding further, Feel free to take a look on the main pieces of code through this [collab notebook](https://colab.research.google.com/drive/1UeGYJcAHDQNUi_Ms1rHBRuHfDa5oHMP7?usp=sharing) 

Do you know what is so great about ***Innopolis*** City ? Well, it is not only a singly thing, but Innopolis is this ever-evolving city where humans and robots live in harmony and peace (well technically robots are saving us the trouble of leaving the comfort of our homes in the harsh Russian winter, but that's just a technicality...) 

Yet, preparing for the darker days, the days where ***MACHINES*** would rebel against the human race, I attempted to build a ***PERSON VS ROBOT*** detector to separate our allies from our enemies. The question now is ***HOW ?***
## BUILDING THE DATASET
### IMAGES
I took the responsibility of collecting enough data for my supreme goal. With the help for several friends I managed to extend my initial dataset of only 50 pictures by $3$ times ending up with a dataset of 150 pictures. (no worries, I have some data augmentation up my sleeves). Maybe we can check a couple of them: 
![image info](https://github.com/ayhem18/Innopolis-Detector/blob/master/documents/p%2Br.jpg?raw=true)
![image info](https://github.com/ayhem18/Innopolis-Detector/blob/master/documents/p1.jpg?raw=true)
![image info](https://github.com/ayhem18/Innopolis-Detector/blob/master/documents/r1.jpg?raw=true)
### Annotations
What about annotations now ? Well [Roboflow](https://roboflow.com/) is the best friend of Computer Vision practitioners (and humanity in general...). The latter is making the procedure quite smoother and much more efficient. Here is our data looks now: 
![annotations](https://github.com/ayhem18/Innopolis-Detector/blob/master/documents/annotated_2.png?raw=true)

### Data Augmentation
Well as you can see in the picture above, some random noise was added to the image. That's part of the data augmentation operations I used to expand the dataset. At this initial version of the project, I experimented with 3 augmentation techniques:
1. Gray scaling
2. Noise: up to $5\%$
3. 90 degree rotations

### Dataset's health
Roboflow performs a health check for the dataset. Hopefully our data does not have any significant issues: 
![](https://github.com/ayhem18/Innopolis-Detector/blob/master/documents/h2.png?raw=true)
Sounds pretty good to me !! let's go
# Building the Detector
## Yolov5
The first model I trained on the custom dataset is the nano-sized Yolov5. The code is commented and explained thoroughly in the accopagning notebooks, but the process can be summarized as follows:
1. installing the dependencies and importing the necessary packages
2. importing the yolob5 version of the custom dataset
3. training and evaluating the model through the scripts provided by Yolov5.

![](https://github.com/ayhem18/Innopolis-Detector/blob/master/documents/seg_test.png?raw=true)

The model performed quite well on the tiny dataset. Certain issues can be resolved with more data (or probably ROBOFLOW PREMIUM ACCOUNT for more augmented data). The details are also considered in the corresponding notebooks.

## Masked RCNN
The first model I trained on the custom dataset is the nano-sized Yolov5. The code is commented and explained thoroughly in the accopagning notebooks, but the process can be summarized as follows:
1. installing detectron2 and importing the necessary packages
2. importing the different functions and modules
3. downloading the dataset in the COCO format for easier registration
4. training and evaluating the model through detectron2 functionalities.

![](https://github.com/ayhem18/Innopolis-Detector/blob/master/documents/mask_rcnn_pred.png?raw=true)

Using such a large model pretty much ensured having quite high performance.
## Models Comparison
YOLOV5 (the nano model) VS FASTER RCNN:
1. Mean Average Precision: 0.698 VS 0.47
2. Inference time: 6.6 ms VS 87 ms
3. Memory Requirements: 28.5 MB VS 3.4 GB

The experiment shows that the yolov5 nano model outperforms Mask RCNN of every single metric: performance, inference and even memory. The models performances are quite likely to be improved with a larger dataset and more augmentation techniques.

# Conclusion
Our small detector was done in Innopolis, from Innopolis to Innopolis. Our small detector here is quite promising. Nevertheless, it is not ready for our futuristic supreme goal. Any feedback, ideas for improvements would be greatly appreciated. 