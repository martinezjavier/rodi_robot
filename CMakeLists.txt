cmake_minimum_required(VERSION 2.8.3)
project(rodi_robot)

find_package(catkin REQUIRED COMPONENTS
  rospy
  geometry_msgs
  sensor_msgs
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

catkin_python_setup()
catkin_package(CATKIN_DEPENDS
  rospy
)

catkin_install_python(PROGRAMS
  nodes/rodi_node
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY
  config
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

if(CATKIN_ENABLE_TESTING)
  find_package(catkin REQUIRED COMPONENTS roslint)
  roslint_python()
  roslint_add_test()
endif()
