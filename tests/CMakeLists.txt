project(ubsan_tests VERSION 0.1 LANGUAGES C CXX)

file(GLOB c_files "*.c" "*.cpp")
foreach(file ${c_files})
  get_filename_component(testname ${file} NAME_WE)
  MESSAGE(STATUS "Test: ${file} ${testname}")
  
  add_executable(${testname} ${file})
 
  target_link_libraries(${testname} PRIVATE ubsan)
  add_dependencies(${testname} ubsan)
  if(${CMAKE_SYSTEM_NAME} STREQUAL Nucleus)
    set(CMAKE_CREATE_NUCLEUS_MAIN 1)
  endif()
endforeach()