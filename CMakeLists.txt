cmake_minimum_required(VERSION 3.28)

project(poc)

find_package(fmt CONFIG REQUIRED)
find_package(antlr4-generator REQUIRED)
find_package(antlr4-runtime REQUIRED)
find_package(LLVM CONFIG REQUIRED)

add_subdirectory(src)

find_package(GTest CONFIG REQUIRED)

include(CTest)
include(GoogleTest)
add_subdirectory(tests)
