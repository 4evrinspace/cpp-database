cmake_minimum_required(VERSION 3.14.0)
project(database VERSION 0.1.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(FLEX REQUIRED)

include_directories(include src ${FLEX_INCLUDE_DIRS})

add_subdirectory(tests)

file(GLOB_RECURSE SOURCES "src/*.cpp")

add_library(database ${SOURCES})
set_target_properties(database PROPERTIES LINKER_LANGUAGE CXX)
target_link_libraries(database PRIVATE stdc++fs)

add_executable(demo demo.cpp)
target_link_libraries(demo PRIVATE database)