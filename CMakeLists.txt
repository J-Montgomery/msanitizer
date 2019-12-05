cmake_minimum_required(VERSION 3.9.6 FATAL_ERROR)

project(libubsan VERSION 0.1 LANGUAGES C)

# ---------------------------------------------------------------------------------------------
# Prepare all files, header and source files.
# ---------------------------------------------------------------------------------------------
include(CMakeLists_Files.txt)

add_library(libubsan STATIC ${ubsan_SOURCES})

target_include_directories(libubsan PUBLIC ${HEADER_ROOT})

if(${CMAKE_BUILD_TYPE} MATCHES Debug)
    add_definitions(-DDEBUG=1)
else()
    add_definitions(-DRELEASE=1)
endif()

add_definitions(-DNUCLEUS=1)
add_compile_options(-fno-short-enums)