# a basic static lib

cmake_minimum_required(VERSION 3.5 FATAL_ERROR)
project(hello-world LANGUAGES CXX)
# generate a library from sources , it is a static lib --- "libmessage.a"
add_library(message
  STATIC
    Message.hpp
    Message.cpp
  )
add_executable(hello-world hello-world.cpp)
#link hello-world.o to "libmessage.a"
target_link_libraries(hello-world message)

