# Specify CMAKE version 
cmake_minimum_required(VERSION 3.16.3)

# Give the project a name. CMake will automativally store this name as the variable PROJECT_NAME
project(Database)

# Add directories where header files can be found
include_directories(${PROJECT_SOURCE_DIR}/include)

# Add subdirectories where CMakeLists.txt can be found
add_subdirectory(${PROJECT_SOURCE_DIR}/tests)
