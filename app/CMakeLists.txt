cmake_minimum_required(VERSION 4.0)
project (my_rest_api LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/bin")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/lib")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/lib")

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Debug")
endif()

add_executable(app src/main.cpp)

add_library(asio INTERFACE)
target_include_directories(asio INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/external/asio/include)
target_link_libraries(app INTERFACE asio)

add_library(Crow INTERFACE)
target_include_directories(Crow INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/external/crow/include)
target_link_libraries(Crow INTERFACE asio)
target_link_libraries(app PUBLIC Crow)

