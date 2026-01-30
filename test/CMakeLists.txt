cmake_minimum_required(VERSION 3.5)

# 添加头文件包含路径
include_directories(${inc_fiber})

# 链接fiber库
link_libraries(fiber_lib)

# 构建测试用例
add_executable(fiber_test fiber_test.cpp)
add_executable(scheduler_test scheduler_test.cpp)
add_executable(iomanager_test iomanager_test.cpp)

# 设置编译选项
set_target_properties(fiber_test PROPERTIES COMPILE_OPTIONS "-pthread")
set_target_properties(scheduler_test PROPERTIES COMPILE_OPTIONS "-pthread")
set_target_properties(iomanager_test PROPERTIES COMPILE_OPTIONS "-pthread")

# 设置链接选项
target_link_libraries(fiber_test pthread dl)
target_link_libraries(scheduler_test pthread dl)
target_link_libraries(iomanager_test pthread dl)