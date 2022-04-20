# 1. a basic CMakeLists.txt
# 2. reference link : https://cmake.org/cmake/help/latest/command/project.html#command:project

# set minimum cmake version
cmake_minimum_required(VERSION 3.5)
# set project command sets variable: PROJECT_NAME ...
project(hello-world)

#prints variable: PROJECT_NAME ...
MESSAGE( STATUS "PROJECT_NAME = ${PROJECT_NAME}.")

#elf file will be hello_elf, sourcefile should be hello-world.c
add_executable(hello_elf hello-world.c)

#can also use variable here
add_executable(${PROJECT_NAME}_2 hello-world.c)
