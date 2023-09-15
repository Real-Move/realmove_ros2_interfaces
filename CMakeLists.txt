cmake_minimum_required(VERSION 3.5)

project(real_move_ros2_interfaces)

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
  # "action/<your_action>.action"

  # "msg/<your_message>.msg"
  "msg/Keypoint.msg"
  "msg/Skeleton.msg"
  "msg/SkeletonArray.msg"

  # "srv/<your_service.srv>"
  DEPENDENCIES builtin_interfaces 
    std_msgs
    geometry_msgs 
  # ADD_LINTER_TESTS
)

# This file defines mappings between ROS 1 and ROS 2 interfaces.
# It is used with the ros1_bridge to allow for communcation between ROS 1 and ROS 2.
# install(FILES mapping_rules.yaml DESTINATION share/${PROJECT_NAME})

ament_export_dependencies(rosidl_default_runtime)
ament_package()
