cmake_minimum_required(VERSION 3.0)
project(YOLOv5-OpenCV-OnnxRunner)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

if (MSVC)
    # Set the MSVC input code encoding format to utf-8
    set(CMAKE_C_FLAGS /source-charset:utf-8)
endif()

message(STATUS "Project: YOLOv5-OpenCV-OnnxRunner")
message(STATUS "Root Path: ${CMAKE_SOURCE_DIR}")

set(OPENCV_DIR  ${CMAKE_SOURCE_DIR}/third_party/opencv480/build)
message(STATUS "OPENCV_DIR Path: ${OPENCV_DIR}")
include_directories(${OpenCV_INCLUDE_DIRS})
include_directories(${OPENCV_DIR}/include)
link_directories("${OPENCV_DIR}/x64/vc16/lib")
set(OpenCV_LIB opencv_world480)


# compile own file
file(GLOB SRC_LIST 
    ${CMAKE_SOURCE_DIR}/*.cpp
)
add_executable(main ${SRC_LIST})
target_compile_features(main PRIVATE cxx_std_17)

target_link_libraries(main ${OpenCV_LIB} ${OpenCV_LIBS})

