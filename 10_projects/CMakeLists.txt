#1. choose cmake versoin as cmakefiles required
cmake_minimum_required(VERSION 2.8)


#2.  project config
##select project-name
set(PROJECT_NAME root-project-name)
set(PROJECT_VERSION "1.0.0.10" CACHE STRING "default project version")

##this is a C/CXX project 
project(${PROJECT_NAME}
    LANGUAGES CXX C
    VERSION ${PROJECT_VERSION}
)

#3. message for cmakefile beginner
message(STATUS "\n########## cmake build for ${PROJECT_NAME}")


#3. option(<variable> "<help_text>" [value])
## option=ON if {valure == ON} else option= {OFF}

option(${PROJECT_NAME}_USE_LIBRARY_shared-mwlib "shared lib for libmw.so" ON 
option(${PROJECT_NAME}_BUILD_app_android "android build" ON)
option(${PROJECT_NAME}_BUILD_kernel "kernel build" ON)
option(${PROJECT_NAME}_BUILD_tools "build tools for target" ON)
option(${PROJECT_NAME}_BUILD_tests "Compiling time tests" ON)
option(${PROJECT_NAME}_BUILD_packages "Packaging for build output" OFF)

## USE_LIBRARY_shared-mwlib handle
include(CMakeDependentOption)
# second option depends on the value of the first
cmake_dependent_option(
  MAKE_STATIC_LIBRARY "Compile sources into a static library" OFF
  "${PROJECT_NAME}_USE_LIBRARY_shared-mwlib" ON
  )
# third option depends on the value of the first
cmake_dependent_option(
  MAKE_SHARED_LIBRARY "Compile sources into a shared library" ON
  "${PROJECT_NAME}_USE_LIBRARY_shared-mwlib" ON
  )




