##############################################################################
# CMake
##############################################################################

cmake_minimum_required(VERSION 2.8.3)
project(py_trees_msgs)

##############################################################################
# Dependencies
##############################################################################

find_package(catkin REQUIRED COMPONENTS
    message_generation
    std_msgs
    uuid_msgs
)

##############################################################################
# Messages
##############################################################################

add_message_files(
  DIRECTORY msg
  FILES
  Behaviour.msg
  BehaviourTree.msg
)

add_service_files(
  DIRECTORY srv
  FILES
  GetBlackboardVariables.srv
  OpenBlackboardWatcher.srv
  CloseBlackboardWatcher.srv
)

generate_messages(DEPENDENCIES std_msgs uuid_msgs)

##############################################################################
# Package
##############################################################################

catkin_package(CATKIN_DEPENDS
    message_runtime
    std_msgs
    uuid_msgs
)
