cmake_minimum_required(VERSION 2.8.3)

project(PTrackingBridge)

set(ROS_BUILD_TYPE Release)

find_package(catkin REQUIRED COMPONENTS geometry_msgs message_generation roscpp std_msgs)

add_message_files(FILES
				  TargetEstimations.msg
)

generate_messages(DEPENDENCIES geometry_msgs std_msgs)

catkin_package(CATKIN_DEPENDS message_runtime
)

include_directories(${catkin_INCLUDE_DIRS})

file(GLOB_RECURSE PTrackingBridge_src "src/*.cpp")

add_executable(PTrackingBridge ${PTrackingBridge_src})
target_link_libraries(PTrackingBridge ${catkin_LIBRARIES})

add_dependencies(PTrackingBridge ${PROJECT_NAME}_generate_messages_cpp)
