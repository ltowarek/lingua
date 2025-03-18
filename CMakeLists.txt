cmake_minimum_required(VERSION 3.28)

project(poc)

find_package(fmt CONFIG REQUIRED)

add_executable(poc poc.cpp)

target_link_libraries(poc fmt::fmt)
