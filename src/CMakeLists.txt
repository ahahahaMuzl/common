cmake_minimum_required(VERSION 3.20)

project(common_test LANGUAGES CXX)

set(app common_test)
set(link_projects)
set(sources_file)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 获取当前目录下所有 .cpp 文件
file(GLOB sources_file ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

# 创建可执行文件
add_executable(${app} ${sources_file})

# 设置包含目录
target_include_directories(${app}
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
)

# 链接库
list(REMOVE_DUPLICATES link_projects)
target_link_libraries(${app}
    PUBLIC
        ${link_projects}
)

# 输出调试信息
message(STATUS "Sources: ${sources_file}")
if(NOT "${link_projects}" STREQUAL "")
    message(STATUS "Linking with: ${link_projects}")
endif()
