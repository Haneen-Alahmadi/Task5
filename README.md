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
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch


#6-Operate TurtleBot3
$ export TURTLEBOT3_MODEL=burger

$roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

#7-open new terminal to Launch the Gmapping SLAM node.

$ export TURTLEBOT3_MODEL=burger

#Install dependent packages on PC if the dependent have already been installed, do the following.

$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

#if it is not installed
#Download and build packages on PC
$ sudo apt update

$ sudo apt install -y python3-wstool python3-rosdep ninja-build stow

$ cd ~/catkin_ws/src

$ wstool init src

$ wstool merge -t src https://raw.githubusercontent.com/cartographer-project/cartographer_ros/master/cartographer_ros.rosinstall

$ wstool update -t src

$ sudo rosdep init

$ rosdep update

$ rosdep install --from-paths src --ignore-src --rosdistro=noetic -y

$ src/cartographer/scripts/install_abseil.sh

$ sudo apt remove ros-noetic-abseil-cpp

$ catkin_make_isolated --install --use-ninja

#Launch the Cartographer SLAM node

$ source ~/catkin_ws/install_isolated/setup.bash

$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=cartographer

#Install dependent packages on PC

$ sudo apt install ros-noetic-slam-karto

#Launch the Karto SLAM node.

$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=karto

#then go to step 7 
#now RViz will open

#8-open new terminal to Run Teleoperation Node
 
$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

#9-open new terminal to save a map

$ rosrun map_server map_saver -f ~/map

#10-Run Navigation Nodes

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

#11-open new terminal to Launch the Navigation

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml


![1](https://user-images.githubusercontent.com/108179353/184265279-c4b7b6a9-8486-471d-bd37-727d1db8b977.jpeg)








![2](https://user-images.githubusercontent.com/108179353/184265304-0235664e-6041-4fa3-b90f-cf071d560d36.jpeg)





