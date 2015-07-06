cmake_minimum_required(VERSION 2.8.3)
project(photo)

set(PKG_DEPS         
roscpp
std_msgs
sensor_msgs
cv_bridge
image_transport
)

set(SRV_FILES
Capture.srv
GetConfig.srv
SetConfig.srv
)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

find_package(OpenCV REQUIRED)
find_package(Boost REQUIRED COMPONENTS timer)
find_package(Gphoto2 REQUIRED libgphoto2)

message(STATUS ${OpenCV_LIBS})

find_package(catkin REQUIRED COMPONENTS ${PKG_DEPS} message_generation)

add_service_files(DIRECTORY srv FILES ${SRV_FILES})

generate_messages(DEPENDENCIES sensor_msgs)

catkin_package(CATKIN_DEPENDS ${PKG_DEPS} message_runtime)

include_directories(include ${Boost_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS} ${Gphoto2_INCLUDE_DIRS} ${OpenCV_INCLUDE_DIRS})

add_subdirectory(src)
