cmake_minimum_required(VERSION 3.5)

# 添加头文件包含路径
include_directories(${inc_fiber})

# 链接fiber库
link_libraries(fiber_lib)

# 构建压测用例
add_executable(fiber_benchmark fiber_benchmark.cpp)
add_executable(scheduler_benchmark scheduler_benchmark.cpp)

# 设置编译选项
set_target_properties(fiber_benchmark PROPERTIES COMPILE_OPTIONS "-pthread")
set_target_properties(scheduler_benchmark PROPERTIES COMPILE_OPTIONS "-pthread")

# 设置链接选项
target_link_libraries(fiber_benchmark pthread dl)
target_link_libraries(scheduler_benchmark pthread dl)