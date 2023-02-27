# Writeup: Track 3D-Objects Over Time

To run our code, we can run at workspace with next command:

```
python loop_over_dataset.py
```

In each exercise, there are different combination of configurations need to use for each point.

### 1. Write a short recap of the four tracking steps and what you implemented there (filter, track management, association, camera fusion). Which results did you achieve? Which part of the project was most difficult for you to complete, and why?

#### Section 1 : Compute Lidar Point-Cloud from Range Image

In this section, the need is to show range image. For this, image have to converted to 8 bit channel in range and intensity, and stack the range and intensity image vertically.

The result will be the following image:

![step1](img/step1.png)

#### Section 2 : Create Birds-Eye View from Lidar PCL

![BEV image](img/step2.PNG)
![Intensity](img/step2_intensity.PNG)

#### Section 3 : Model-based Object Detection in BEV Image

![BEV image](img/step3.PNG)
![Intensity image](img/step3_intensity.PNG)

To create **labels vs detected** image, in **loop_over_dataset.py**  results_fullpath variable must to be modified because path generated was not correct.

At image can observe the cars inside bounding boxes.
![Labels vs detected](img/step3_labels_vs_detected.PNG)

#### Section 4 : Performance Evaluation for Object Detection

To get statistics, all window visualization has been commented to avoid to press right key in all images.
At statistics, 

With **use_labels_as_objects = False** results obtained are:

```
precision = 0.9506578947368421, recall = 0.9444444444444444
```

![!use_labels_as_objects](img/graphs1.png)

With **use_labels_as_objects = True** results obtained are:

```
precision = 1.0, recall = 1.0
```

![use_labels_as_objects](img/graphs2.png)

### 2. Do you see any benefits in camera-lidar fusion compared to lidar-only tracking (in theory and in your concrete results)? 

Mixing different sensor more data can be achieved. Improvements can help to locate better other objects, giving option to get better decisions.


### 3. Which challenges will a sensor fusion system face in real-life scenarios? Did you see any of these challenges in the project?

Position achieved for each device can be different and this can produce to system having a bad decisions. Using **iou** value can be reduce this problem, but if system has not enough precision, can't be reliable.


### 4. Can you think of ways to improve your tracking results in the future?

Filtering results of sensor data can improve all system. Also, camara training in all conditions and lot of different configurations, can help to be prepared for further problems.