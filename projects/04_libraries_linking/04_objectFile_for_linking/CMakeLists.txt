# object lib, used for build lib

cmake_minimum_required(VERSION 3.5 FATAL_ERROR)
project(hello-world LANGUAGES CXX)

# generate an object library from sources
add_library(message-objs
  OBJECT
    Message.hpp
    Message.cpp
  )

# this is only needed for older compilers
# but doesn't hurt either to have it
set_target_properties(message-objs
  PROPERTIES
    POSITION_INDEPENDENT_CODE 1
  )
# obj lib -> shared lib "libmessage.so"
add_library(message-shared
  SHARED
    $<TARGET_OBJECTS:message-objs>
  )
set_target_properties(message-shared
  PROPERTIES
    OUTPUT_NAME "message"
  )
# obj lib -> static lib "libmessage.a"
add_library(message-static
  STATIC
    $<TARGET_OBJECTS:message-objs>
  )
set_target_properties(message-static
  PROPERTIES
    OUTPUT_NAME "message"
  )

add_executable(hello-world hello-world.cpp)
#link to target , not lib name
target_link_libraries(hello-world message-static)

