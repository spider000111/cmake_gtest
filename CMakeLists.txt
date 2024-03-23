cmake_minimum_required(VERSION 3.14)

set(This Example)

project(${This} C CXX)

# GoogleTest requires at least C++14
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)





set(CMAKE_POSITION_INDEPENDENT_CODE ON)

enable_testing()


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
