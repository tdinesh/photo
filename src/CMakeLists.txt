
add_library(photo2 libphoto2/photo_reporter.cpp libphoto2/photo_camera_list.cpp libphoto2/photo_camera.cpp libphoto2/photo_image.cpp)
target_link_libraries(photo2 ${Gphoto2_LIBRARIES} ${OpenCV_LIBS})

add_executable(photo_node photo_node/photo_node.cpp)
target_link_libraries(photo_node photo2)

target_link_libraries(photo_node ${catkin_LIBRARIES})
