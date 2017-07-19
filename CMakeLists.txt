cmake_minimum_required(VERSION 2.8.3)
project(nmea_driver)

find_package(catkin REQUIRED COMPONENTS roslint std_msgs message_generation)

catkin_python_setup()

add_message_files(
  FILES
  Sentence.msg
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

catkin_package(CATKIN_DEPENDS std_msgs message_runtime)

install(PROGRAMS
   scripts/nmea_serial_driver
   scripts/nmea_topic_driver
   scripts/nmea_topic_serial_reader
   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

# Check package for pep8 style, add a test to fail on violations.
roslint_python()
roslint_add_test()
