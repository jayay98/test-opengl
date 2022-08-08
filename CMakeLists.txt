# CMakeLists.txt
cmake_minimum_required(VERSION 3.0)
project(test)

find_package(glfw3 CONFIG REQUIRED)
find_package(GLEW REQUIRED)

add_executable(main main.cpp)

target_link_libraries(main PRIVATE glfw)
target_link_libraries(main PRIVATE GLEW::GLEW)