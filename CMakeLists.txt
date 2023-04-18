cmake_minimum_required(VERSION 3.16)
project(csandbox)

add_executable(${PROJECT_NAME} src/main.cc)

find_package(fmt REQUIRED)
include_directories(${fmt_INCLUDE_DIR})
target_link_libraries(${PROJECT_NAME} fmt::fmt)