cmake_minimum_required(VERSION 4.0.0)

set(CXX_DISABLE_WERROR 1)
set(CMAKE_CXX_STANDARD 11)

set(PROJECT_NAME NewFSMController)
set(PROJECT_DESCRIPTION "NewFSMController")
set(PROJECT_URL "")

project(
  ${PROJECT_NAME}
  LANGUAGES CXX
  VERSION 1.0.0)
include(CTest)
enable_testing()

if(NOT TARGET mc_rtc::mc_control)
  find_package(mc_rtc REQUIRED)
endif()

add_subdirectory(src)

configure_file(etc/NewFSMController.in.yaml
               "${CMAKE_CURRENT_BINARY_DIR}/etc/NewFSMController.yaml")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/etc/NewFSMController.yaml"
        DESTINATION "${MC_CONTROLLER_RUNTIME_INSTALL_PREFIX}/etc")
