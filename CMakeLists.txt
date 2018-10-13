##############################################################################
# CMake
##############################################################################

cmake_minimum_required(VERSION 3.5)
project(py_trees_msgs)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

##############################################################################
# Dependencies
##############################################################################

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)
# find_package(actionlib_msgs REQUIRED)
# find_package(dynamic_reconfigure REQUIRED)
find_package(std_msgs REQUIRED)
# find_package(uuid_msgs REQUIRED)

##############################################################################
# Messages
##############################################################################

#generate_dynamic_reconfigure_options(
#    dynamic_reconfigure/Battery.cfg
#    dynamic_reconfigure/MockActionServer.cfg
#    dynamic_reconfigure/MockSafetySensors.cfg
#)
#
#add_action_files(
#  DIRECTORY
#      action
#  FILES
#      Dock.action
#      Rotate.action
#)
#
#set(msg_files
#  "msg/Behaviour.msg"
#  "msg/BehaviourTree.msg"
#)
#rosidl_generate_interfaces(${PROJECT_NAME}
#  ${msg_files}
#  DEPENDENCIES
#    actionlib_msgs
#    std_msgs
#    uuid_msgs
#  ADD_LINTER_TESTS
#)

set(srv_files
  "srv/GetBlackboardVariables.srv"
  "srv/OpenBlackboardWatcher.srv"
  "srv/CloseBlackboardWatcher.srv"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${srv_files}
  ADD_LINTER_TESTS
)
##############################################################################
# Package
##############################################################################

ament_export_dependencies(rosidl_default_runtime)

ament_package()