
add_library(photo2 libphoto2/photo_reporter.cpp libphoto2/photo_camera_list.cpp libphoto2/photo_camera.cpp libphoto2/photo_image.cpp)
target_link_libraries(photo2 ${Gphoto2_LIBRARIES} ${OpenCV_LIBS})

add_executable(photo_node photo_node/photo_node.cpp)
target_link_libraries(photo_node photo2)

target_link_libraries(photo_node ${catkin_LIBRARIES})

add_executable(photo_node_pub photo_node/photo_node_publish.cpp)
target_link_libraries(photo_node_pub photo2)

target_link_libraries(photo_node_pub ${catkin_LIBRARIES})

install(TARGETS photo_node_pub photo2
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
