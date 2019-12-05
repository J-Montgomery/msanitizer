project(ubsan VERSION 0.1 LANGUAGES C)

# ---------------------------------------------------------------------------------------------
# Prepare all files, header and source files.
# ---------------------------------------------------------------------------------------------
include(CMakeLists_Files.txt)

add_library(ubsan STATIC ${UBSAN_SOURCES} ${UBSAN_HEADERS})

target_include_directories(ubsan PUBLIC ${HEADER_ROOT})

target_compile_options(ubsan PUBLIC  -fno-short-enums)
target_compile_options(ubsan PRIVATE -Werror)
target_compile_options(ubsan PRIVATE -Wpedantic)
