# AI_Radiologist
## Why AI in Radiology?
Diseases and injuries to the bone are the major contributing factors in causing abnormalities in bones. Whenever there is an injury to the bone, the physician asks you to do an X-Ray, thus when such hundreds of patients visit hospitals everyday there are massive numbers of X-rays done on a regular basis. To be specific with the stats, Musculoskeletal conditions affect more than 1.7 billion people worldwide, and are the most common cause of severe, long-term pain and disability, with 30 million emergency department visits annually and increasing. So, in order to reduce the error rate of the Radiologist and to do the analysis much faster, an AI solution should suffice the purpose. 

## About Dataset
Dataset used in this project is called MURA. MURA is one of the largest public radiographic image datasets. MURA is a dataset of musculoskeletal radiographs consisting of 14,863 studies from 12,173 patients, with a total of 40,561 multi-view radiographic images. Each belongs to one of seven standard upper extremity radiographic study types: elbow, finger, forearm, hand, humerus, shoulder, and wrist. 

## Data Analysis
+-------------------------------+
|Body_Part |	Label | Img_Count	|
+-------------------------------+
|ELBOW 	   |   0 	  |   2925    |
|          |   1 	  |   2006    |
|FINGER 	 |   0 	  |   3138    |
|          |   1 	  |   1968    |
|FOREARM 	 |   0 	  |   1164    |
|          |   1 	  |    661    |
|HAND 	   |   0 	  |   4059    |
|          |   1 	  |   1484    |
|HUMERUS 	 |   0 	  |    673    |
|          |   1 	  |    599    |
|SHOULDER  |   0 	  |   4211    |
|          |   1 	  |   4168    |
|WRIST 	   |   0 	  |   5765    |
|          |   1 	  |   3987    |
+-------------------------------+

## Image Preprocessing
The most of the X_Ray image has more black space and X_Ray content is located at the center of the image. So, i need only th eX-Ray content & will eliminate the unwanted areas. To do this, i build a method called "Content Based Image Retrieval using edge detection"

STEP 1: Morph close ((OpenCV lib)
STEP 2: Adaptive histogram equalization (step 1 & 2 helps to suppress the text in th eimage)
STEP 3: Edge Finder (using canny)
STEP 4: Based on th edge detected, cropping the image (Content Based Image Retrieval using edge detection)

BEFORE IMAGE PROCESSING:

AFTER IMAGE PROCESSING:

## Modelling
Using Densenet201 architecture

TRAIN ACCURACY : 90% VAL ACCURACY: 80%

## Visualizing the abnormal area using GradCam
STEP 1: Create a model that map the input to the activation layer of last convolution layer to final class prediction
INPUT IMG: 

STEP 2: Compute the gradient of the top predicted class for our input image
STEP 3: Get the gradient of the top predicted class with regard to the output feature map of the last conv layer
STEP 4: We multiply each channel in the feature map array by "how important this channel is" with regard to the top predicted class
STEP 5: The channel-wise mean of the resulting feature map is our heatmap of class activation
STEP 6: Now Generate the class activation heatmap
HEAT MAP:

STEP 7: Superimpose the heatmap on original image
RESULT IMG:


