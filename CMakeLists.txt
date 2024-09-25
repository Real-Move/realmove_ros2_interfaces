cmake_minimum_required(VERSION 3.5)
project(realmove_ros2_interfaces)

# Default to C++17
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# Interfaces dependencies
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "action/Calibrate.action"
  "msg/ArucoMarker.msg"
  "msg/ArucoMarkerArray.msg"
  "msg/Keypoint.msg"
  "msg/Skeleton.msg"
  "msg/SkeletonArray.msg"
  "msg/Object.msg"
  "msg/ObjectArray.msg"
  "msg/Object3D.msg"
  "msg/ObjectArray3D.msg"
  "msg/SkeletonDescriptionArray.msg"
  "srv/String.srv"

  DEPENDENCIES 
    builtin_interfaces 
    std_msgs
    geometry_msgs 

  ADD_LINTER_TESTS
)

# This file defines mappings between ROS 1 and ROS 2 interfaces.
# It is used with the ros1_bridge to allow for communcation between ROS 1 and ROS 2.
# install(FILES mapping_rules.yaml DESTINATION share/${PROJECT_NAME})

ament_export_dependencies(rosidl_default_runtime)
ament_package()
