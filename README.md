# Autonomous_driving_application_Car_detection

In this notebook, we'll implement object detection using the very powerful YOLO model. Many of the ideas in this notebook are described in the two YOLO papers: Redmon et al., 2016 and Redmon and Farhadi, 2016.

By the end of this project, we'll be able to:

Detect objects in a car detection dataset
Implement non-max suppression to increase accuracy
Implement intersection over union
Handle bounding boxes, a type of image annotation popular in deep learning

# 1 - Problem Statement
We are working on a self-driving car. Go you! As a critical component of this project, you'd like to first build a car detection system. To collect data, you've mounted a camera to the hood (meaning the front) of the car, which takes pictures of the road ahead every few seconds as you drive around.

Pictures taken from a car-mounted camera while driving around Silicon Valley.
Dataset provided by drive.ai.
You've gathered all these images into a folder and labelled them by drawing bounding boxes around every car you found. Here's an example of what your bounding boxes look like:

![image](https://github.com/user-attachments/assets/69f263e2-94b1-4db3-80dd-06c0970ca4e1)


Figure 1: Definition of a box
If there are 80 classes you want the object detector to recognize, you can represent the class label 
 either as an integer from 1 to 80, or as an 80-dimensional vector (with 80 numbers) one component of which is 1, and the rest of which are 0. The video lectures used the latter representation; in this notebook, you'll use both representations, depending on which is more convenient for a particular step.

In this project, we'll discover how YOLO ("You Only Look Once") performs object detection, and then apply it to car detection. Because the YOLO model is very computationally expensive to train, the pre-trained weights are already loaded for you to use.

"You Only Look Once" (YOLO) is a popular algorithm because it achieves high accuracy while also being able to run in real time. This algorithm "only looks once" at the image in the sense that it requires only one forward propagation pass through the network to make predictions. After non-max suppression, it then outputs recognized objects together with the bounding boxes.
