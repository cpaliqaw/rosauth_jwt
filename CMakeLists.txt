cmake_minimum_required(VERSION 3.0.2)
project(rosauth_jwt)

find_package(catkin REQUIRED COMPONENTS std_msgs rosbridge_msgs)

catkin_python_setup()

catkin_package(CATKIN_DEPENDS rospy rosbridge_msgs)

# do not wildcard install files since the root folder of the package will contain a debian folder for releasing
catkin_install_python(PROGRAMS
  src/rosauth_jwt/rosauth_jwt.py
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(FILES
  launch/rosauth_jwt.launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

if(CATKIN_ENABLE_TESTING)
  find_package(rostest REQUIRED)
  add_rostest(test/test-rosauth-jwt-node.launch)
endif()