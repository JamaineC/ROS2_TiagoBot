cmake_minimum_required(VERSION 3.8)
project(jac105_ros360_cpp)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(OpenCV REQUIRED)
find_package(image_transport REQUIRED)
find_package(cv_bridge REQUIRED)
find_package(tf2 REQUIRED)
find_package(tf2_ros REQUIRED)
find_package(control_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)
find_package(rclcpp_action REQUIRED)
find_package(rclcpp_components REQUIRED)
find_package(moveit_ros_planning_interface REQUIRED)

add_executable(helloWorld src/helloWorld.cpp)
add_executable(examplePublisher src/exampleSubscriber.cpp)
add_executable(exampleSubscriber src/exampleSubscriber.cpp)
add_executable(velodyneSub src/velodyneSub.cpp)
add_executable(PMB2PubSub src/PMB2PubSub.cpp)
add_executable(colourFinder src/colourFinder.cpp)
add_executable(colourClient src/colourClient.cpp)
add_executable(headNdepth src/headNdepth.cpp)
add_executable(tiagoController src/tiagoController.cpp)

target_include_directories(helloWorld PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>)
target_compile_features(helloWorld PUBLIC c_std_99 cxx_std_17)  # Require C99 and C++17

include_directories(${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIBRARY_DIRS})
add_definitions(${OpenCV_DEFINITIONS})

ament_target_dependencies(helloWorld rclcpp sensor_msgs geometry_msgs)
ament_target_dependencies(examplePublisher rclcpp std_msgs)
ament_target_dependencies(exampleSubscriber rclcpp std_msgs)
ament_target_dependencies(velodyneSub rclcpp sensor_msgs)
ament_target_dependencies(PMB2PubSub rclcpp sensor_msgs geometry_msgs)
ament_target_dependencies(colourFinder rclcpp sensor_msgs geometry_msgs)
ament_target_dependencies(colourClient rclcpp rcl_interfaces)
ament_target_dependencies(headNdepth rclcpp sensor_msgs geometry_msgs image_transport cv_bridge OpenCV tf2 tf2_ros control_msgs trajectory_msgs rclcpp_components rclcpp_action)
ament_target_dependencies(tiagoController rclcpp sensor_msgs geometry_msgs image_transport cv_bridge OpenCV tf2 tf2_ros control_msgs trajectory_msgs rclcpp_components rclcpp_action moveit_ros_planning_interface)



install(TARGETS 
helloWorld
examplePublisher
exampleSubscriber
velodyneSub
PMB2PubSub
colourFinder
colourClient
headNdepth
tiagoController
  DESTINATION lib/${PROJECT_NAME})

install(DIRECTORY
launch
DESTINATION share/${PROJECT_NAME})

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
