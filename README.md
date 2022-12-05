# Udacity self driving car Localization using scan matching

## Background
Scan matching localization techniques compared 2 similar lidar scans and calculated a transform matrix which further determines the change in position.
In this project we have pre-defined PCL map within Carla simulator. The Self driving car equiped with Lidar performs lidar scans and the scans are compared with the map scans to determine the position of the self driving car in the map environment.

#Scan matching algorithms used
#1. ICP : iterative closest point .ICP has a target scan and a source scan.
  step1 : Associations are made between the source points and target points
  step2 : A transform that minimizes the sum of association's distances is performed
  step3 : Steps 1 and 2 repeat until associations don't change, and ICP has converged or a certain number of iterations have been done.
  
  in our project the source scan  is the scan from the on board lidar and the target scan is the map pcl from HD maps.
  
#2. NDT : Normal distribution transform
The first part of the Normal Distributions Transforms (NDT) is to create a probability density function (PDF):
1.Find the centroid of the cluster region
2.Find the covariance of the cluster
3.Use the cluster region's centroid and its covariance to define the probability function

![image](https://user-images.githubusercontent.com/32779283/205695210-6f63ebfd-ec85-402e-bc0d-dfb56a83e55c.png)

The next part of NDT is to utilize Newton's Method:

Newton's method gives a direction to take to get to the root of a function or a higher/smaller value
With a multi-variable function the gradient and hessian matrices are used to do Newton's method
![image](https://user-images.githubusercontent.com/32779283/205695502-626da82b-b371-4a17-a1ee-b771f0882ac8.png)

## Project Requirement: 
The goal will be to localize a car driving in simulation for at least 170m from the starting position and never exceeding a distance pose error of 1.2m. The simulation car is equipped with a lidar, provided by the simulator at regular intervals are lidar scans. There is also a point cloud map map.pcd already available, and by using point registration matching between the map and scans localization for the car can be accomplished. This point cloud map has been extracted from the CARLA simulator.

## ICP Results
From the course introduction we can know the NDT is more accurate than the ICP in most of the situation.But we still spend much to study the ICP method. The ICP is easy to understand, more direct for logical to absorb. It is like the track association in the lidar object detection charpter. 

I took much time on tuning the iterations, filter resolution and scan rate. Finally the iteration =30, the filer resolution = 0.6 and scan rate= 5000, their combination cause the better result. It can achieve the requirement Max.error 1.2m.

![icppassed](https://user-images.githubusercontent.com/32779283/205695804-d0495435-7d85-4003-a544-862a79779516.jpg)

## NDT Results
Ref : https://knowledge.udacity.com/questions/832405
NDT parameters:
ndt.setTransformationEpsilon(1e-3);
ndt.setResolution(5); 
ndt.setMaximumIterations(100);

Iterations = 30

![ndtpassed](https://user-images.githubusercontent.com/32779283/205695903-ae195845-0122-4f3b-aefd-afec5184251b.jpg)


## Acknowledgement
All mentors in Udacity and all students on the knowledge platform, your answers and support gives me great help. Appreciate all of you.
