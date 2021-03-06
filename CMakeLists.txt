cmake_minimum_required( VERSION 2.8 )
PROJECT(mscnav)

set(Ceres_DIR /opt/thirdparty/lib/cmake/Ceres)

find_package(glog REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(OpenCV REQUIRED)
find_package(Ceres REQUIRED)

SET(CMAKE_CXX_COMPILE "g++")
SET(CMAKE_C_COMPILE "gcc")
SET( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -march=native -O2 -pthread" )
SET( CMAKE_BUILD_TYPE "release")

SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
SET(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

INCLUDE_DIRECTORIES(/opt/thirdparty/install/include)

INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/include 
                    ${PROJECT_SOURCE_DIR}/submodules/tools/include
                    ${PROJECT_SOURCE_DIR}/thirdparty
                    ${EIGEN3_INCLUDE_DIRS}
                    ${OpenCV_INCLUDE_DIRS})
MESSAGE(STATUS "Eigen include: ${EIGEN3_INCLUDE_DIRS}")
MESSAGE(STATUS "OpenCV include: ${OpenCV_INCLUDE_DIRS}")
MESSAGE(STATUS "Ceres include: ${CERES_INCLUDE_DIRS}")
       
add_subdirectory(${PROJECT_SOURCE_DIR}/thirdparty)
add_subdirectory(${PROJECT_SOURCE_DIR}/submodules/tools)
add_subdirectory(${PROJECT_SOURCE_DIR}/src/filter)
add_subdirectory(${PROJECT_SOURCE_DIR}/src/imu)
add_subdirectory(${PROJECT_SOURCE_DIR}/src/camera)
add_subdirectory(${PROJECT_SOURCE_DIR}/src/data)
add_subdirectory(${PROJECT_SOURCE_DIR}/src/process)
add_subdirectory(${PROJECT_SOURCE_DIR}/test)
