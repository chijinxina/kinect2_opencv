cmake_minimum_required(VERSION 3.9)
project(kinect2_opencv)

# 添加c++ 11标准支持
set( CMAKE_CXX_FLAGS "-std=c++11" )

# 添加cmake_modules
list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake_modules)

# 添加库文件输出路径
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

# 添加可执行文件输出路径
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

###################dependencies#######################
# 寻找OpenCV库
find_package( OpenCV 3.3.0 REQUIRED )
find_package(freenect2 REQUIRED)

message(OpenCV: ${OpenCV_VERSION})
message(freenect2 include: ${freenect2_INCLUDE_DIR})
message(freenect2 library: ${freenect2_LIBRARIES})
#message(boost include: ${BOOST_INCLUDE_DIR})
#message(boost library: ${BOOST_LIBRARIES})


# 添加头文件
include_directories(
        ${OpenCV_INCLUDE_DIRS}
        ${freenect2_INCLUDE_DIR}
        #${BOOST_INCLUDE_DIR}
)
include_directories("/usr/include/libusb-1.0/")

# 添加依赖库
set(THIRD_PARTY_LIBS
        ${OpenCV_LIBS}
        ${freenect2_LIBRARIES}
        )

#######################SubCmakeList#############################
add_subdirectory(src)
