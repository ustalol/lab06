cmake_minimum_required(VERSION 3.10)
project(solver)

install(TARGETS solver_application DESTINATION bin)

add_executable(solver equation.cpp)

target_link_libraries(solver PRIVATE
    formatter_ex_lib
    solver_lib
)
