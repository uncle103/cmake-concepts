cmake_minimum_required(VERSION 3.5)

# Set a default C++ compile flag
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DEX2" CACHE STRING "Set C++ Compiler Flags" FORCE)
project (compile_flags)

add_executable(cmake_examples_compile_flags main.cpp)

#user can also specify cxx flags via:
#cmake -DCMAKE_CXX_FLAGS="-DEX2"

