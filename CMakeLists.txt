cmake_minimum_required(VERSION 3.0)

project(OpenGLSandbox)


find_package(OpenGL REQUIRED)

add_subdirectory(external)

include_directories(
	external/AntTweakBar-1.16/include/
	external/glfw-3.1.2/include/GLFW/
	external/glm-0.9.7.1/
	external/glew-1.13.0/include/
	external/assimp-3.0.1270/include/
	external/bullet-2.81-rev2613/src/
	.
)

set(ALL_LIBS
	${OPENGL_LIBRARY}
	glfw
	GLEW_1130
)

add_definitions(
	-DTW_STATIC
	-DTW_NO_LIB_PRAGMA
	-DTW_NO_DIRECT3D
	-DGLEW_STATIC
	-D_CRT_SECURE_NO_WARNINGS
)

set(project_glsl 
	shaders/default.vs
	shaders/default.frag)

set(project_sources 
	src/main.cpp
	src/shader.cpp)

set(project_headers
	src/shader.h)

add_executable(${PROJECT_NAME} ${project_sources} ${project_headers} ${project_glsl})

target_link_libraries(${PROJECT_NAME} ${ALL_LIBS})
