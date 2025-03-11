# utbots_dependencies
Simple repository for custom ROS dependecies -- messages, services and actions -- which multiple utbots repositories need. Designed to avoid having to install multiple packages to work on a singular one

### Building
```
cd ~/<ros2_ws>/src
git clone https://github.com/UtBotsAtHome-UTFPR/utbots_dependencies.git
cd ..
colcon build
```

### Dependencies

Make sure ROS is installed along with the ordinary message types (std_msgs, sensor_msgs, geometry_msgs, etc.).

## Adding new resources
Make sure the .msg, .action or .srv follows the syntax guidelines for ROS2: 
- For the file name, only *CamelCase*
- For the file fields names, only *snake_case*
- Message types should have their full "path", such as std_msgs/Header not only Header

### utbots_msgs
- Define <new_msg>.msg inside *utbots_msgs/msg* with the custom message fields
- Add it to the CMakeLists.txt:
```
rosidl_generate_interfaces(${PROJECT_NAME}
  ...
  "msg/<new_msg>.msg"
  DEPENDENCIES <remember to add new missing dependencies if necessary>
)
```
- Build with `colcon build` in the workspace base directory

### utbots_srvs
- Define <new_srv>.msg inside *utbots_srvs/msg* with the custom message fields
- Make sure the syntax for .srv files is like the following:
```
# Request
## Add your request fieds, if any
---
# Response
## Add your response fieds, if any
```
- Add it to the CMakeLists.txt:
```
rosidl_generate_interfaces(${PROJECT_NAME}
  ...
  "srv/<new_srv>.srv"
  DEPENDENCIES <remember to add new missing dependencies if necessary>
)
```
- Build with `colcon build` in the workspace base directory


### utbots_actions
- Define <new_action>.action inside *utbots_actions/msg* with the custom message fields
- Make sure the syntax for .action files is like the following:
```
# Goal
## Add your goal fieds, if any
---
# Result
## Add your result fieds, if any
---
# Feedback
## Add your feedback fieds, if any
```
- Add it to the CMakeLists.txt:
```
rosidl_generate_interfaces(${PROJECT_NAME}
  ...
  "action/<new_action>.action"
  DEPENDENCIES <remember to add new missing dependencies if necessary>
)
```
- Build with `colcon build` in the workspace base directory