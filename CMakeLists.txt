cmake_minimum_required(VERSION 3.5)

project(glad)

find_package(OpenGL REQUIRED)

add_library(${PROJECT_NAME} STATIC
    src/gl.c
    include/glad/gl.h
    include/KHR/khrplatform.h
)

target_include_directories(${PROJECT_NAME}
PUBLIC
    include
)

target_link_libraries(${PROJECT_NAME}
INTERFACE
    OpenGL::GL
)
