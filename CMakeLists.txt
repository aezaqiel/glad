cmake_minimum_required(VERSION 3.10)

project(glad
    LANGUAGES C
    DESCRIPTION "OpenGL Core 4.6 Loader (glad)"
)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

find_package(OpenGL REQUIRED)

add_library(glad STATIC
    ${CMAKE_CURRENT_SOURCE_DIR}/src/gl.c
)

target_sources(glad
PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/include/glad/gl.h
    ${CMAKE_CURRENT_SOURCE_DIR}/include/KHR/khrplatform.h
PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/src/gl.c
)

target_include_directories(${PROJECT_NAME}
PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)

target_link_libraries(glad
PUBLIC
    OpenGL::GL
)

if(UNIX)
    target_link_libraries(glad PUBLIC ${CMAKE_DL_LIBS})
endif()

source_group("Sources" FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/src/gl.c
)

source_group("Headers" FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/include/glad/gl.h
    ${CMAKE_CURRENT_SOURCE_DIR}/include/KHR/khrplatform.h
)
