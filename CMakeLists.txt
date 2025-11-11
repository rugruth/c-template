
cmake_minimum_required(VERSION 3.10)

# Project will be named after the current directory name
get_filename_component(PROJECT_NAME_VAR ${CMAKE_CURRENT_SOURCE_DIR} NAME)
project(${PROJECT_NAME_VAR})

set(CMAKE_C_STANDARD 11)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out)
file(MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/out)

add_executable(${PROJECT_NAME_VAR} src/main.c)
option(BUILD_SHARED_LIBS "Build using shared libraries" OFF)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
target_compile_options(${PROJECT_NAME_VAR} PRIVATE -g)
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
target_compile_options(${PROJECT_NAME_VAR} PRIVATE -O3)
endif()

