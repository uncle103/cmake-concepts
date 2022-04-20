# fortran language

cmake_minimum_required(VERSION 3.5 FATAL_ERROR)
# specify fortran language
project(hello-world LANGUAGES Fortran)
add_executable(hello-world hello-world.f90)

