# Extended Kalman Filter Project

The goal of this project is to utilize a kalman filter to estimate the state of a moving object of interest with noisy lidar and radar measurements. The root mean square error (RMSE) values calculated by taking into account the state estimation and the ground truth should is required to be lower than the tolerance outlined in the [project rubric](https://review.udacity.com/#!/rubrics/748/view). 

[//]: # (Image References)

[image1]: ./project_img/OnlyRadar.jpg "Estimation with Radar"
[image2]: ./project_img/OnlyLidar.jpg "Estimation with Lidar"
[image3]: ./project_img/LidRad_Data1.jpg "Estimation with Radar & Lidar Data 1"
[image4]: ./project_img/LidRad_Data2.jpg "Estimation with Radar & Lidar Data 2"

This project involves the Term 2 Simulator which can be downloaded [here](https://github.com/udacity/self-driving-car-sim/releases)

This repository includes two files that can be used to set up and install [uWebSocketIO](https://github.com/uWebSockets/uWebSockets) for either Linux or Mac systems. For windows you can use either Docker, VMware, or even [Windows 10 Bash on Ubuntu](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) to install uWebSocketIO. Please see the uWebSocketIO Starter Guide page in the classroom within the EKF Project lesson for the required version and installation scripts.

Once the install for uWebSocketIO is complete, the main program can be built and run by doing the following from the project top directory.

1. mkdir build
2. cd build
3. cmake ..
4. make
5. ./ExtendedKF

Tips for setting up your environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)

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

Here is the main protcol that main.cpp uses for uWebSocketIO in communicating with the simulator.


INPUT: values provided by the simulator to the c++ program

["sensor_measurement"] => the measurement that the simulator observed (either lidar or radar)


OUTPUT: values provided by the c++ program to the simulator

["estimate_x"] <= kalman filter estimated position x
["estimate_y"] <= kalman filter estimated position y
["rmse_x"]
["rmse_y"]
["rmse_vx"]
["rmse_vy"]

In the simulator, one can find Data Set 1 which is above referred data set. Data set 2 is also included which is a reversed version of Data set 1. Also the second data set starts with a radar measurement where as the first data set starts with a lidar measurement. 

The simulator is used to project estimation along side the sensor measurements and simulatneously displays the RMSE.

Using just the Radar measurement data for estimation, the RMSE and estimation path observed can be seen in the image below.
![alt text][image1]

Using just the Lidar measurement data for estimation, the RMSE and estimation path observed can be seen in the image below.
![alt text][image2]

It may be noted that the RMSE is more for estimation using Radar than Lidar perhaps owing to low spatial resolution of Radar data.

Using both the Lidar and Radar measurement data (dataset 1) for estimation, the RMSE and estimation path observed can be seen in the image below.
![alt text][image3]

It may be noted that the RMSE in this case is less than RMSEs observed in case of estimations with either one of the sensors.

Using both the Lidar and Radar measurement data (dataset 2) for estimation, the RMSE and estimation path observed can be seen in the image below.
![alt text][image4]

---

## Other Important Dependencies

* cmake >= 3.5
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make` 
   * On windows, you may need to run: `cmake .. -G "Unix Makefiles" && make`
4. Run it: `./ExtendedKF `

[Reference Repository](https://github.com/udacity/CarND-Extended-Kalman-Filter-Project)

