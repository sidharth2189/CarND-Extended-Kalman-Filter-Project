# Extended Kalman Filter Project

The goal of this project is to utilize a kalman filter to estimate the state of a moving object of interest with noisy lidar and radar measurements. The root mean square error (RMSE) values calculated by taking into account the state estimation and the ground truth is required to be lower than the tolerance outlined in the [project rubric](https://review.udacity.com/#!/rubrics/748/view). 

[//]: # (Image References)

[image1]: ./project_img/OnlyRadar.jpg "Estimation with Radar"
[image2]: ./project_img/OnlyLidar.jpg "Estimation with Lidar"
[image3]: ./project_img/LidRad_Data1.jpg "Estimation with Radar & Lidar Data 1"
[image4]: ./project_img/LidRad_Data2.jpg "Estimation with Radar & Lidar Data 2"

The project repository contains:

main.cpp - communicates with the Term 2 Simulator receiving data measurements, calls a function to run the Kalman filter, calls a function to calculate RMSE (src folder)

FusionEKF.cpp - initializes the filter, calls the predict function, calls the update function (src folder)

kalman_filter.cpp- defines the predict function, the update function for lidar, and the update function for radar (src folder)

tools.cpp- function to calculate RMSE and the Jacobian matrix (src folder)

obj_pose-laser-radar-synthetic-input.txt - Lidar and Radar data (data folder)
Each row represents a sensor measurement where the first column tells if the measurement comes from radar (R) or lidar (L).

For a row containing radar data, the columns are: 
sensor_type, rho_measured, phi_measured, rhodot_measured, timestamp, x_groundtruth, y_groundtruth, vx_groundtruth, vy_groundtruth, yaw_groundtruth, yawrate_groundtruth.

For a row containing lidar data, the columns are: sensor_type, x_measured, y_measured, timestamp, x_groundtruth, y_groundtruth, vx_groundtruth, vy_groundtruth, yaw_groundtruth, yawrate_groundtruth

In the simulator, one can find Data Set 1 which is above referred data set. Data set 2 is also included which is a reversed version of Data set 1. Also the second data set starts with a radar measurement where as the first data set starts with a lidar measurement. 

The simulator is used to project estimation along side the sensor measurements and simulatneously displays the RMSE.
Using just the Radar measurement data for estimation, the RMSE and estimation path observed can be seen in the image below. The specified RMSE tolerance is not met.

![alt text][image1]


Using just the Lidar measurement data for estimation, the RMSE and estimation path observed can be seen in the image below. It may be noted that the RMSE is more for estimation using Radar than Lidar perhaps owing to low spatial resolution of Radar data. The specified RMSE tolerance is not met.

![alt text][image2]


Using both the Lidar and Radar measurement data (dataset 1) for estimation, the RMSE and estimation path observed can be seen in the image below. It may be noted that the RMSE in this case is less than RMSEs observed in case of estimations with either one of the sensors. The specified RMSE tolerance has been met.

![alt text][image3]


Using both the Lidar and Radar measurement data (dataset 2) for estimation, the RMSE and estimation path observed can be seen in the image below. The specified RMSE tolerance has been met.

![alt text][image4]

---

For dependencies and build instruction proceed to the [Reference Repository](https://github.com/udacity/CarND-Extended-Kalman-Filter-Project)

