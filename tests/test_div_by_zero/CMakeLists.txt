set(TEST_ROOT ${CMAKE_CURRENT_SOURCE_DIR})

file(GLOB files "*.c" "*.h" "*.cpp" "*.hpp")
get_filename_component(testname ${TEST_ROOT} NAME_WE)

add_executable(${testname} ${files})

target_link_libraries(${testname} PRIVATE ubsan)
add_dependencies(${testname} ubsan)

if(${CMAKE_SYSTEM_NAME} STREQUAL Nucleus)
set(CMAKE_CREATE_NUCLEUS_MAIN 1)
endif()