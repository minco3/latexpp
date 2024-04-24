cmake_minimum_required(VERSION 3.26)
project(latexpp)

set(CXX_STANDARD 23)

add_compile_definitions(-DV8_COMPRESS_POINTERS)
add_compile_definitions(-DV8_ENABLE_SANDBOX)
add_compile_definitions(-Dv8_use_external_startup_data=true)

add_library(LaTeX latex.cpp latex.hpp)
target_link_libraries(LaTeX v8)
target_link_libraries(LaTeX v8_libbase)
target_link_libraries(LaTeX v8_libplatform)
target_link_libraries(LaTeX wkhtmltox)

add_executable(main main.cpp)
target_link_libraries(main LaTeX)