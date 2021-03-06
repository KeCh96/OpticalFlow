cmake_minimum_required(VERSION 2.8)
project(OpticalFlow)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake-modules)
set(OpenCV_DIR /home/lshi/Application/Anaconda/share/OpenCV/)
message(${CMAKE_MODULE_PATH})
find_package(OpenCV REQUIRED)
message(${OpenCV_INCLUDE_DIRS})
message(${OpenCV_LIBS})
include_directories(${OpenCV_INCLUDE_DIRS})

set(SOURCE_FILES_VIDEO cal_optical_flow_from_video.cpp cal_optical_flow.cpp list_file.cpp)
set(SOURCE_FILES_IMG cal_optical_flow_from_img.cpp cal_optical_flow.cpp list_file.cpp mkdir.cpp mkdir.h)
set(SOURCE_FILES_TEST test.cpp cal_optical_flow.cpp list_file.cpp)

add_executable(calOpticalFlowFromImg ${SOURCE_FILES_IMG})
add_executable(calOpticalFlowFromVideo ${SOURCE_FILES_VIDEO})
add_executable(testMethod ${SOURCE_FILES_TEST})

target_link_libraries(calOpticalFlowFromImg ${OpenCV_LIBS})
target_link_libraries(calOpticalFlowFromVideo ${OpenCV_LIBS})
target_link_libraries(testMethod ${OpenCV_LIBS})