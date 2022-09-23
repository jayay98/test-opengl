# CMakeLists.txt
cmake_minimum_required(VERSION 3.0)
project(test)

include_directories(.)

find_package(glfw3 CONFIG REQUIRED)
find_package(GLEW CONFIG REQUIRED)
find_package(glm CONFIG REQUIRED)

add_executable(tut_01 tut_01/main.cpp)
add_executable(tut_02 
	tut_02/main.cpp 
	common/shader.cpp 
	common/shader.hpp

	shaders/SimpleFragmentShader.glsl
	shaders/SimpleVertexShader.glsl
)

set(ALL_LIBS glfw GLEW::GLEW glm::glm)
target_link_libraries(tut_01 PRIVATE ${ALL_LIBS})
target_link_libraries(tut_02 PRIVATE ${ALL_LIBS})