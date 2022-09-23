# CMakeLists.txt
cmake_minimum_required(VERSION 3.0)
project(test)

include_directories(.)

find_package(glfw3 CONFIG REQUIRED)
find_package(GLEW CONFIG REQUIRED)
find_package(glm CONFIG REQUIRED)

# sets the COMMON variable to the list of .cpp of .hpp file names
file(GLOB_RECURSE COMMON common/*.?pp LIST_DIRECTORIES false)
# The executables will be inside ./build/bin
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ./bin)
add_executable(tut_01 tut_01/main.cpp)
add_executable(tut_02 
	tut_02/main.cpp 
	${COMMON}

	shaders/SimpleFragmentShader.glsl
	shaders/SimpleVertexShader.glsl
)
add_executable(tut_03 
	tut_03/main.cpp 
	${COMMON}

	shaders/SimpleFragmentShader.glsl
	shaders/SimpleTransformVertexShader.glsl
)

set(ALL_LIBS glfw GLEW::GLEW glm::glm)
target_link_libraries(tut_01 PRIVATE ${ALL_LIBS})
target_link_libraries(tut_02 PRIVATE ${ALL_LIBS})
target_link_libraries(tut_03 PRIVATE ${ALL_LIBS})