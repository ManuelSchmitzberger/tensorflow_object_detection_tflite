cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(Demo_Project)

set(CMAKE_CXX_STANDARD 14)
set(REQUIRED_LIBS ${TFLITE_LIBS})

find_package(OpenCV REQUIRED core highgui calib3d features2d photo)
find_package(Threads REQUIRED)
find_library(TFLITE_LIBRARY tensorflowlite "lib")
#find_library(TFLITE_LIBRARY tensorflow-lite "lib")
include_directories("include")

set(REQUIRED_LIBS "stdc++fs")
list(APPEND REQUIRED_LIBS ${TFLITE_LIBRARY})
list(APPEND REQUIRED_LIBS ${OpenCV_LIBS})
#list(APPEND REQUIRED_LIBS ${Threads_LIBS})

set(CMAKE_C_FLAGS "-pthread")
set(SOURCE_FILES Demo.cpp)

add_executable("Demo" ${SOURCE_FILES})
#SET_TARGET_PROPERTIES(Demo PROPERTIES LINK_FLAGS "-no-pie")
target_link_libraries("Demo" ${REQUIRED_LIBS} -lpthread)

