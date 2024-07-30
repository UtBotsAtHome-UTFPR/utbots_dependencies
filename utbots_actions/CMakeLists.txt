cmake_minimum_required(VERSION 3.0.2)
project(utbots_actions)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  
  nav_msgs
  roscpp
  rospy
  std_msgs
  vision_msgs
  sensor_msgs
  actionlib_msgs
)

################################################
## Declare ROS messages, services and actions ##
################################################

## Generate actions in the 'action' folder
add_action_files(
  DIRECTORY action/vision_action 
  
  FILES
  ## Vision
  recognition.action
  new_face.action
  train.action
  
)
add_action_files(
  DIRECTORY action/voice_action

  FILES
  ## Voice
  InterpretNLU.action
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  sensor_msgs nav_msgs std_msgs vision_msgs actionlib_msgs
)

###################################
## catkin specific configuration ##
###################################
catkin_package(
  CATKIN_DEPENDS actionlib_msgs
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)
