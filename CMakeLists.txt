cmake_minimum_required(VERSION 2.8)
project(test_tensorflow_cpp)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# add modules
list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake/Modules")
list(APPEND CMAKE_MODULE_PATH "/usr/local/share/eigen3/cmake")

# find packages
find_package(TensorFlow REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(Protobuf REQUIRED)
set(PROJECT_INCLUDE_DIRS ${} ${Eigen_INCLUDE_DIRS} ${PROTOBUF_INCLUDE_DIRS})
set(PROJECT_LIBRARIES ${TensorFlow_LIBRARIES} ${PROTOBUF_LIBRARIES})

file(GLOB_RECURSE SRC_FILES "src/*.cpp" "src/*.h" "src/*.inl" )

add_executable(${PROJECT_NAME} ${SRC_FILES})

include_directories(${TensorFlow_INCLUDE_DIRS})
include_directories(${EIGEN3_INCLUDE_DIR})
include_directories(${Protobuf_INCLUDE_DIRS})

target_link_libraries(${PROJECT_NAME} ${TensorFlow_LIBRARIES})
target_link_libraries(${PROJECT_NAME} ${Protobuf_LIBRARIES})
