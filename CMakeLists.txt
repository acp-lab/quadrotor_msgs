cmake_minimum_required(VERSION 3.8)
project(quadrotor_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find build tools and runtime dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# Dependencies used in the .msg files
find_package(std_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

# Declare message files (relative to 'msg/' directory)
set(message_list
  "msg/TrajectoryPoint.msg"
  "msg/PositionCommand.msg"
)

# Message generation
rosidl_generate_interfaces(${PROJECT_NAME}
  ${message_list}
  DEPENDENCIES std_msgs geometry_msgs nav_msgs
)

ament_export_dependencies(
  std_msgs
  geometry_msgs
  nav_msgs
  rosidl_default_runtime
)

ament_package()