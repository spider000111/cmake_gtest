
cmake_minimum_required(VERSION 3.00)

set(This Exampletests)

set(
    Sources
    Exampletests.cpp
)

add_executable(${This} ${Sources})

target_link_libraries(${This} PUBLIC
    gtest_main
    Example
    #to compile this i need these libs from outside
)

add_test(
    NAME ${This}
    COMMAND ${This}
)
