cmake_minimum_required(VERSION 3.10)
project(Application)

# Add the source files
add_executable(Application application.cpp src/glad.c)

# Include directories
include_directories(include)

# Add GLFW
# set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
# set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
# set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)

add_subdirectory(glfw-3.4)
target_link_libraries(Application glfw)
target_link_libraries(Application opengl32) # Add OpenGL library on Windows

