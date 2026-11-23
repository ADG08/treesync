cmake_minimum_required(VERSION 3.31)
project(treesync)
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
enable_testing()
add_executable(treesync)
include(FetchContent)

FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/a46a6012a133c7c0929fdae55b321c2fe65f3c5f.zip
)
FetchContent_MakeAvailable(googletest)

target_compile_options(treesync
    PRIVATE
    -Wall
    -Wextra
    -Wpedantic
    -Wconversion
)

set_property(TARGET treesync PROPERTY COMPILE_WARNING_AS_ERROR ON)
include(GoogleTest)

add_executable(
    treesync_test
    tests/file_descriptor_test.cpp
)

target_link_libraries(treesync_test
    PRIVATE
    gtest_main
)
target_compile_options(treesync_test
    PRIVATE
    -Wall
    -Wextra
    -Wpedantic
    -Wconversion
)
set_property(TARGET treesync_test PROPERTY COMPILE_WARNING_AS_ERROR ON)

gtest_discover_tests(treesync_test)

target_sources(treesync
    PRIVATE
    src/main.cpp
)