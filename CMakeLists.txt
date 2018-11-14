cmake_minimum_required(VERSION 2.8.12)
project(inotify-cpp)

set(CMAKE_CXX_FLAGS "-std=c++11 -m32")


enable_testing()

set(CMAKE_CXX_STANDARD 11)

set(
  CMAKE_CXX_FLAGS_DEBUG
  "${CMAKE_CXX_FLAGS_DEBUG} -Wall -Wextra -Wpedantic -g3 -O0"
)

###############################################################################
# Boost
###############################################################################
find_package(
  Boost 1.53.0
  COMPONENTS system filesystem unit_test_framework
  REQUIRED
)
include_directories(SYSTEM ${Boost_INCLUDE_DIRS})

if(${INOTIFY_CLANG_COVERAGE})
    set(CMAKE_CXX_FLAGS "-fprofile-instr-generate -fcoverage-mapping")
endif()

if(${INOTIFY_GCC_COVERAGE})
    set(CMAKE_CXX_FLAGS "-g -O0 -fprofile-arcs -ftest-coverage")
endif()

add_subdirectory(source)
add_subdirectory(test)
