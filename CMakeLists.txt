cmake_minimum_required(VERSION 3.31)
project(treesync)
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
add_executable(treesync)

target_compile_options(treesync
    PRIVATE
    -Wall
    -Wextra
    -Wpedantic
    -Wconversion
)

set_property(TARGET treesync PROPERTY COMPILE_WARNING_AS_ERROR ON)

target_sources(treesync
    PRIVATE
    src/main.cpp
)
