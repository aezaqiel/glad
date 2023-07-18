cmake_minimum_required(VERSION 3.5)

project(glad C)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON CACHE INTERNAL "" FORCE)
set(CMAKE_C_STANDARD 99)

add_library(${PROJECT_NAME} STATIC
    src/gl.c
    include/glad/gl.h
    include/KHR/khrplatform.h
)

target_include_directories(${PROJECT_NAME}
PUBLIC
    include
)
