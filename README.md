# Task5
Use Turtlebot3 with SLAM approach to create and save a map

#1-Install ROS on Remote PC

$ sudo apt update

$ sudo apt upgrade

$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh

$ chmod 755 ./install_ros_noetic.sh 

$ bash ./install_ros_noetic.sh

#2-Install Dependent ROS Packages

$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
  
#3-Install TurtleBot3 Packages
  
$ sudo apt install ros-noetic-dynamixel-sdk

$ sudo apt install ros-noetic-turtlebot3-msgs

$ sudo apt install ros-noetic-turtlebot3

#4-Install Simulation Package

$ cd ~/catkin_ws/src/

$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git

$ cd ~/catkin_ws && catkin_make

#5-Launch Simulation World 

$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
 #-TurtleBot3 World

#6-Operate TurtleBot3

$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
