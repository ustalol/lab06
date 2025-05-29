cmake_minimum_required(VERSION 3.10)
project(formatter_lib)

add_library(formatter_lib STATIC formatter.cpp)

target_include_directories(formatter_lib PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}
)

install(TARGETS formatter_lib
        ARCHIVE DESTINATION lib)
install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/formatter.h
        DESTINATION include)
