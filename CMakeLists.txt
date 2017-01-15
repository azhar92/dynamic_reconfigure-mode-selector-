cmake_minimum_required(VERSION 2.8.3)
project(dynamic_tutorials)

find_package(catkin REQUIRED COMPONENTS
  dynamic_reconfigure
  rospy
)

#add dynamic reconfigure api

## Generate dynamic reconfigure parameters in the 'cfg' folder
generate_dynamic_reconfigure_options(
   cfg/Tutorials.cfg
   #cfg/DynReconf1.cfg
   #cfg/DynReconf2.cfg
 )

catkin_package(
  CATKIN_DEPENDS dynamic_reconfigure rospy
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)


## Declare a C++ executable
 add_executable(dynamic_tutorials_node src/dynamic_tutorials_node.cpp)

# make sure configure headers are built before any node using them
add_dependencies(turtlesim ${PROJECT_NAME}_gencfg)

