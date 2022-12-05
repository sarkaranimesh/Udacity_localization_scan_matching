# Self_Driving_C3_Scan_Matching_Localization

## Requirement: 
The goal will be to localize a car driving in simulation for at least 170m from the starting position and never exceeding a distance pose error of 1.2m. The simulation car is equipped with a lidar, provided by the simulator at regular intervals are lidar scans. There is also a point cloud map map.pcd already available, and by using point registration matching between the map and scans localization for the car can be accomplished. This point cloud map has been extracted from the CARLA simulator.

## ICP Results
From the course introduction we can know the NDT is more accurate than the ICP in most of the situation.But we still spend much to study the ICP method. The ICP is easy to understand, more direct for logical to absorb. It is like the track association in the lidar object detection charpter. 

I took much time on tuning the iterations, filter resolution and scan rate. Finally the iteration =30, the filer resolution = 0.6 and scan rate= 5000, their combination cause the better result. It can achieve the requirement Max.error 1.2m.

![ICP result](https://github.com/junjiexu628/Self_Driving_C3_Scan_Matching_Localization/blob/main/images/project_icp12_iter30_resp65.png)

## NDT Results
I thought NDT method will be much easier than ICP method to acheive the target. But it also took much much time to tune, tried much combination of ndt parameters, such as ndt.setResolution, ndt.setTransformationEpsilon, ndt.setStepSize, filter resolution and iterations. Finally I achieved the target at the help of the mentor.

![NDT result](https://github.com/junjiexu628/Self_Driving_C3_Scan_Matching_Localization/blob/main/images/project_NDT_170m_res1.png)

## Acknowledgement
All mentors in Udacity and all students on the knowledge platform, your answers and support gives me great help. Appreciate all of you.
