cmake_minimum_required(VERSION 3.1)
project(cpprestsdk-root NONE)
enable_testing()

# Include our extra modules
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/)

add_subdirectory(Release)
