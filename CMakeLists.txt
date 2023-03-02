cmake_minimum_required(VERSION 3.21)
get_filename_component(ProjectName ${CMAKE_CURRENT_SOURCE_DIR} NAME)
project(${ProjectName} C CXX)
set(CMAKE_C_STANDARD 17)
set(CMAKE_CXX_STANDARD 17)
add_compile_options(-Wall -Wextra -Wshadow -Wpedantic)
enable_testing()

# Avoid warnings in CMake 3.24.0:
if (CMAKE_VERSION VERSION_GREATER "3.24.0")
    cmake_policy(SET CMP0135 NEW)
endif ()

# Google Test
include(FetchContent)
FetchContent_Declare(
        googletest
        URL https://github.com/google/googletest/archive/2d4f208765af7fa376b878860a7677ecc0bc390a.zip
)
FetchContent_MakeAvailable(googletest)
include(GoogleTest)

# Include directories
include_directories(src/include)

# Executable
add_executable(${PROJECT_NAME} src/main.c)

#add_executable(example_test example.c test/example_test.cpp)
#target_link_libraries(example_test gtest_main)

# Tests
#gtest_discover_tests(example_test)
