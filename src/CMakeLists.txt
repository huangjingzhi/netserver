# 定义项目的最低CMake版本
cmake_minimum_required(VERSION 2.8)

# 定义工程名称和版本
project(netserver)

# 设置C++标准
set(CMAKE_CXX_STANDARD 11)
# set(CMAKE_CXX_STANDARD_REQUIRED True)

# 包含子目录
# add_subdirectory(server)  # 这里添加src目录中的CMakeLists.txt

# 包含头文件目录
include_directories(${PROJECT_SOURCE_DIR}/server)

set(SOURCES
    server/ConnectManage.cpp
    server/NetIoManage.cpp
    server/NetIoWorker.cpp
    main.cpp
)

# 设置CMAKE_BUILD_TYPE为Debug
set(CMAKE_BUILD_TYPE Debug)
add_compile_options(-g)
add_compile_options(-std=gnu++11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x -g -Wall -O0 -Wno-unused-variable -pthread")


# add_compile_options(-lpthread)
# add_compile_options(-Wl,--no-as-needed)
# set_target_properties(netserver PROPERTIES
#                       COMPILE_FLAGS "-g"
#                       LINK_FLAGS "-g")

add_executable(netserver ${SOURCES})

# 可选：定义安装目标、测试、外部依赖等
