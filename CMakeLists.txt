cmake_minimum_required(VERSION 3.16)

project(MMeterProject VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_BUILD_TYPE Release)

if(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
    add_compile_options(-Wall -Wextra -Wpedantic -Werror)
endif()

file(GLOB_RECURSE SOURCES "src/*.cpp")

add_library(MMeter STATIC ${SOURCES})

target_include_directories(MMeter PUBLIC 
    ${PROJECT_SOURCE_DIR}/include
)

add_executable(MMeterTest tests/Test.cpp)
target_link_libraries(MMeterTest PRIVATE MMeter)