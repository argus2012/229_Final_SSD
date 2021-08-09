# **Application of Deep Learning in Autonomous Driving System**

## Autonomous Driving System

With the increasing penetration of ADAS in new cars, such as, ACC (Adaptive Cruise Control), LDW (Lane Departure Warning), and AVP (Automated Valet Parking), these kinds of ADAS functions are being more and more popular. Meanwhile, self-driving cars are being tested on public roads by some giant technology and carmaker companies, such as Waymo, Baidu and GM. Self-driving Robotaxis are taking off in many cities in China and US.

![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/baidu.png)  
**Baidu Apollo Robotaxi in Beijing**  
*Picture Source: Baidu*  

The most critical factor of the au'tonomous driving system is Data. The data of the real road testings. Absolutely, the data come from all kinds of sensors. We need multiple sensors, such as cameras, radars, Lidars, and HD maps, to detect the environment around the vehicles, even the information from the transport infrastructure, for example, the V2X technology makes connected cars to communicate with other vehicles and even anything else.  
![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/AV%20car.png)  
*Picture Source: Endeavor Business Media.*

As we know, the au'tonomous driving system is composed of sense, perceive, decide, and actuate, these four layers. And most AI technology applied in perception and decide layers.  
![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/AS.png)  
*Picture Source: Arm Limited*

In my point of view, **sensor fusion** is one of the most key technical points to the success of au'tonomous driving system.  Because each sensor has its own advantages and disadvantages, for example, from the vision system, it is easy to recognize the type of target from the colorful image, and from the radar system, we can get the information about object's speed and position, and from the Lidar system, we can retrieve more accurate distance information. So, after sensor fusion, We can combine all the advantages to get better recognition results.  
![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/SensorFusion.png)  
**Sensor Fusion in AD Perception**  
*Picture Source: medium.com*

## Object Detection Algorithm  
Recent years, Object Detection by vision system, such as single camera or Stereo /ˈsterioʊ/ Camera is still the most widely used Deep Learning technology, and with the most performance improvement.
Typically, there are four components of an object detection framework: Region proposal, Feature extraction and network predictions, Non-maximum suppression (NMS), and Evaluation metrics.  

![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/OD.png)  
*Picture Source: Analytics Vidhya*  

**Two-Stage:**

The detection of R-CNN family models has two stages: First, the model proposes a set of  ROI, regions of interest by Selective Search or Regional Proposal Network (RPN) according to the potential bounding box candidates. Then only based on the candidate region, we process the classifier.

**One-Stage:**

But this kind of Network is too slow at inference time. So One-stage detectors, such as the SSD and Yolo, were proposed later. The image is passed once through the network to predict the confidence score and the object class. We can see here, the single shot detectors are much faster than two-stage detectors.  

![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/OD_Algorithm.png)  
*Picture Source: SSD: Single Shot MultiBox Detector (slides)*  

## SSD: Single Shot MultiBox Detector
* Good balance between speed and accuracy
* Prior Box (Anchor Box)
* Feature maps of various scales
* Hard Negative Mining

![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/SSD_PriorBox.png)  

![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/SSD_Structure.png)  
*Source: SSD: Single Shot MultiBox Detector*  

## Implementation on Embedded Platform
This is the implementation of the SSD model based on embedded system, for example the automotive grade platform, Renesas RCar V3H (eCube). 
I applied the pre-trained SSD caffe model, via the frontend CNN tools provided by Renesas, to convert the caffe model to binary files which can be used by Hardware accelerators. 

![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/Embedded.png)  
*Picture Source: Renesas*  

We are testing this platform with the real-time images directly from the camera. And we can get the output with the bounding boxes. 
![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/Renesas.png)  

## Project Demo
My implementation based on pre-trained SSD model. I am Testing on the dataset of VOC2007. For this project I just Detect the objects with the classes of **Bicycle, Bus, Car, Motorbike, Person, Train** that related to the transportation on the real road.  
![image](https://github.com/argus2012/229_Final_SSD/blob/master/img/Pascal.png)  

![image](https://github.com/argus2012/229_Final_SSD/blob/master/out_images/000252_out.jpg)  
![image](https://github.com/argus2012/229_Final_SSD/blob/master/out_images/001447_out.jpg)  
![image](https://github.com/argus2012/229_Final_SSD/blob/master/out_images/test1_out.jpg)  

Project codes also refer to [here](https://drive.google.com/drive/folders/1RynaKIjnvfzoRUB0iEADHJX3vm-1C1ej?usp=sharing)
