cmake_minimum_required(VERSION 3.2.2)


set(CMAKE_CXX_COMPILER "g++")
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(cmake/HunterGate.cmake)

HunterGate(
    URL "https://github.com/Goganych/hunter/archive/v0.19.137.1.tar.gz"
    SHA1 "2193dcd2972d8f299818a237a516d04de2e52984"
    LOCAL
)

project(pack)
hunter_add_package(yaml-cpp)
find_package(yaml-cpp CONFIG REQUIRED)

add_executable(pack ${CMAKE_CURRENT_SOURCE_DIR}/sources/pack.cpp)
target_link_libraries(pack yaml-cpp::yaml-cpp)
add_executable(unpack ${CMAKE_CURRENT_SOURCE_DIR}/sources/unpack.cpp)
target_link_libraries(unpack yaml-cpp::yaml-cpp)