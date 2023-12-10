cmake_minimum_required(VERSION 3.00)

set(This Example)

project(${This} C CXX)

set(CMAKE_POSITION_INDEPENDENT_CODE ON)

enable_testing()

add_subdirectory(googletest)

set(Headers 
    src/Example.hpp
    src/dep.hpp
)

set(
    Sources
    src/Example.cpp
    src/dep.cpp
)

add_library(${This} ${Headers} ${Sources})  #i am creating library named Example with headers and source

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)

add_subdirectory(test)

add_executable(main_custom src/main.c)
