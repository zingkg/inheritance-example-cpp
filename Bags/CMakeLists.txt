cmake_minimum_required(VERSION 2.8)
set(CMAKE_LEGACY_CYGWIN_WIN32 0)

project(Bags)

set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_CXX_FLAGS "-Wall -g -std=c++11")
message("Making with CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS}")

set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_BINARY_DIR}/Output/Install)

file(GLOB WEISS_SRC RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} "Weiss/*.cpp")
file(GLOB BAGS_SRC RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} "Bags/*.cpp")
file(GLOB MAIN_SRC RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} "Main/*.cpp")
add_executable(Bags ${WEISS_SRC} ${BAGS_SRC} ${MAIN_SRC})
set_target_properties(Bags PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/Output)

enable_testing(true)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/Tests/)
