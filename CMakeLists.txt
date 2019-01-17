cmake_minimum_required(VERSION 3.0)
project(ladybug_msgs)

add_compile_options(-std=c++14 -Wall -Werror)

find_package(catkin REQUIRED COMPONENTS
        message_generation
        sensor_msgs
        std_msgs
        )

#include_directories(
#    ${catkin_INCLUDE_DIRS}
#)
#Generate messages in the 'msg' folder
add_message_files(DIRECTORY msg
        FILES
        LadybugTiles.msg
        )

# Generate added messages and services with any dependencies listed here
generate_messages(
        DEPENDENCIES
        std_msgs
        sensor_msgs
)

catkin_package(
        CATKIN_DEPENDS message_runtime sensor_msgs std_msgs
)


install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
        FILES_MATCHING PATTERN "*.h")
