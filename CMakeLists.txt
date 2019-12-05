cmake_minimum_required(VERSION 3.9.6 FATAL_ERROR)

if(${CMAKE_BUILD_TYPE} MATCHES Debug)
    add_definitions(-DDEBUG=1)
else()
    add_definitions(-DRELEASE=1)
endif()

add_definitions(-DNUCLEUS=1)

add_subdirectory(ubsan)
add_subdirectory(tests)