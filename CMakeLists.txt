cmake_minimum_required(VERSION 3.10.0)

project(libexprpr)

find_library(MATH_LIB m)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -O3")

set(SOURCE_FILES
        exprpr.h
        exprpr.c
    )

add_library(exprpr STATIC ${SOURCE_FILES})

target_link_libraries(exprpr ${MATH_LIB})
install(TARGETS exprpr ARCHIVE DESTINATION lib)
install(FILES exprpr.h DESTINATION include COMPONENT Devel)

add_executable(example example.c exprpr.c)
target_link_libraries(example ${MATH_LIB})
