cmake_minimum_required(VERSION 2.8.12)

project(Example)
include(CTest)

include(cmake/DownloadProject/DownloadProject.cmake)
download_project(PROJ                googletest
                 GIT_REPOSITORY      https://github.com/google/googletest.git
                 GIT_TAG             master
                 UPDATE_DISCONNECTED 1 
)

add_subdirectory(${googletest_SOURCE_DIR} ${googletest_BINARY_DIR})

add_executable(example example.cpp)
target_link_libraries(example gtest gmock_main)
add_test(NAME example_test COMMAND example)
