# a basic shared lib

cmake_minimum_required(VERSION 3.5)
project(hello_library)
#Generate the shared library from the library sources, that is --- "libhello_library.so"
add_library(hello_library SHARED
    src/Hello.cpp
)
# name hello::library is the same as hello_library
add_library(hello::library ALIAS hello_library)

target_include_directories(hello_library
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
)
add_executable(hello_binary
    src/main.cpp
)
# link the new hello_library target with the hello_binary target
target_link_libraries( hello_binary
    PRIVATE
        hello::library
)

