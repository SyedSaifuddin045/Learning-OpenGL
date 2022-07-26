cmake_minimum_required(VERSION 3.0.0)
project (OpenglSetup)

set (CMAKE_EXPORT_COMPILE_COMMANDS ON)
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror -std=c++17")

set (include_dir "${PROJECT_SOURCE_DIR}/include/")
set (libraries "${PROJECT_SOURCE_DIR}/lib/")
set (source_dir "${PROJECT_SOURCE_DIR}/src/")

link_directories(${libraries})
file (GLOB source_files "${source_dir}/*.cpp" "${source_dir}/*.c")
file (GLOB header_files "${include_dir}/*.h" "${include_dir}/glad/gald.h" "${include_dir}/GLFW/glfw3.h")

include_directories(${libraries})
include_directories(${include_dir})

add_executable(OpenglSetup ${source_files} ${header_files})
find_package(glfw3 3.3 REQUIRED) 
target_link_libraries(OpenglSetup PUBLIC GL dl glfw X11 Xrandr Xi)