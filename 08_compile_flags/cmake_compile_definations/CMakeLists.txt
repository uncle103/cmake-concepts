cmake_minimum_required(VERSION 3.5)

# Set the project name
project (compile_flags)

# Add an executable
add_executable(cmake_examples_compile_flags main.cpp)
#equals to "gcc/g++ -D EX3" when build target cmake_examples_compile_flags
target_compile_definitions(cmake_examples_compile_flags
    PRIVATE EX3
)

