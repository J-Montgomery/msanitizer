project(ubsan_tests VERSION 0.1 LANGUAGES C CXX)

macro(subdirlist result curdir)
  file(GLOB children RELATIVE ${curdir} ${curdir}/*)
  set(dirlist "")
  foreach(child ${children})
    if(IS_DIRECTORY ${curdir}/${child})
      list(APPEND dirlist ${child})
    endif()
  endforeach()
  set(${result} ${dirlist})
endmacro()

subdirlist(subdirs ${CMAKE_CURRENT_SOURCE_DIR})
MESSAGE(STATUS "subdirs: ${subdirs}")

foreach(subdir ${subdirs})
  add_subdirectory(${subdir})
endforeach()