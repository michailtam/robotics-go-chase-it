# Robotics Simulation - Go Chase It
In this robotics simulation a custom *mobile robot* chases a white ball which gets placed by the user in an office building
in [gazebo](http://gazebosim.org/). The robot uses a camera to determine if there is a white ball or not and a laser scanner ([Lidar](https://en.wikipedia.org/wiki/Lidar)) to map the building. The interactions of the robot get implemented using [ROS-Kinetic](https://www.ros.org/) and C++. To track what the robot sees and senses the 3D visualization tool [Rviz tool for ROS](http://wiki.ros.org/rviz) gets used. 

### Feutures
- Only white balls are getting chased (e.g. if the robot sees red ball it stops)
- The robot changes its direction based on odometry measurements
- When there is no ball in its view range, the robot stops immediately
- To get the image from the camera the robot subscribes to the **/camera/rgb/image_raw topic**
- To get the data from the laser scanner the robot subsrcibes to the **/scan topic**
- The supported laser scanners in ROS are [these](http://wiki.ros.org/Sensors#A2D_range_finders) here

### Prerequisites
This project assumes that you are using Ubuntu (tested on Ubuntu 20.4 LST) and that ROS, gazebo and all required packages
are installed.

### Installation
To install the repository follow the following steps:

1. Clone the repository ```$ git clone https://github.com/michailtam/go-chase-it.git```
2. Create the **src** folder in the catkin_workspace ```$ mkdir -p go-chase-it/.Project2/src```
3. Copy the **my_robot** and **ball_chaser** directories to the src folder and initialize the workspace
```
$ cd go-chase-it/.Project2/
$ mv my_robot/ src && mv ball_chaser/ src
$ cd src
$ catkin_init_workspace
```
4. Return to the toplevel of the catkin workspace and build the workspace
```
$ cd ..
$ catkin_make
```

### Running the simulation
To run the simulation follow the following steps:

1. Open a terminal change into the toplevel of the catkin workspace and issue
```
$ source devel/setup.bash
$ roslaunch my_robot world.launch
```
2. Open a second terminal (also change to toplevel) and issue
```
$ source devel/setup.bash
$ roslaunch ball_chaser ball_chaser.launch
```

The overall process to run the simulation and to setup up Rviz accordingly are also shown in the video bekow.

#### Video
<a href="https://www.youtube.com/embed/0WqCSpGcEX0" target="_blank">
<img src="https://github.com/michailtam/go-chase-it/blob/master/img/go-chase-it.png" alt="Go Chase It (ROS) Video" width="760" height="488" border="0" />