#

cmake_minimum_required(VERSION 3.5)
project(hello_library)
#Generate the static library from the library sources --- "libhello_library.a"
add_library(hello_library STATIC
    src/Hello.cpp
)
#libhello_library.a or any elf that links to libhello_library.a automatically set -I ${PROJECT_SOURCE_DIR}/include
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
        hello_library
)

