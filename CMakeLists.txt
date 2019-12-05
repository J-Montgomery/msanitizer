cmake_minimum_required(VERSION 3.9.6 FATAL_ERROR)

project(ubsan VERSION 0.1 LANGUAGES C)

# ---------------------------------------------------------------------------------------------
# Prepare all files, header and source files.
# ---------------------------------------------------------------------------------------------
include(CMakeLists_Files.txt)

add_library(ubsan STATIC ${UBSAN_SOURCES} ${UBSAN_HEADERS})

target_include_directories(ubsan PUBLIC ${HEADER_ROOT})

if(${CMAKE_BUILD_TYPE} MATCHES Debug)
    add_definitions(-DDEBUG=1)
else()
    add_definitions(-DRELEASE=1)
endif()

add_definitions(-DNUCLEUS=1)
add_compile_options(-fno-short-enums)