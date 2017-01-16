cmake_minimum_required(VERSION 2.8.3)
project(dynamic_tutorials)

find_package(catkin REQUIRED COMPONENTS
  dynamic_reconfigure
  rospy
#  std_msgs
#  message_generation
)

#CMAKE_py_LINK_EXECUTABLE()

#add (dynamic reconfigure api)

#add_message_files(
#   FILES
#   Tutorials.msg
#)

#generate_messages(
#   DEPENDENCIES
#   std_msgs
#)

generate_dynamic_reconfigure_options(
   cfg/Tutorials.cfg
 )

###################################
## catkin specific configuration ##
###################################
catkin_package(CATKIN_DEPENDS dynamic_reconfigure rospy)

#include_directories(
#  ${catkin_INCLUDE_DIRS}
#)


add_executable(dynamic_tutorials_node nodes/server.py)

add_dependencies(dynamic_tutorials_node ${PROJECT_NAME}_gencfg)

set_target_properties(dynamic_tutorials_node PROPERTIES LINKER_LANGUAGE CMAKE_py_LINK_EXECUTABLE)

#target_link_libraries(dynamic_tutorials_node
# ${catkin_LIBRARIES}
#)
