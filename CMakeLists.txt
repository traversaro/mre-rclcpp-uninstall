cmake_minimum_required(VERSION 3.16)

project(MREUninstallTarget)

install(FILES empty.file DESTINATION share/MREUninstallTarget)

add_subdirectory(subdir)

# uninstall target 
# See https://gitlab.kitware.com/cmake/community/-/wikis/FAQ#can-i-do-make-uninstall-with-cmake
if(NOT TARGET uninstall)
  message(STATUS "Defining top-level uninstall target")
  configure_file(
    "${CMAKE_CURRENT_SOURCE_DIR}/cmake_uninstall.cmake.in"
    "${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake"
    IMMEDIATE @ONLY)

  add_custom_target(uninstall
    COMMAND ${CMAKE_COMMAND} -P ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake)
else()
   message(STATUS "Not defining top-level uninstall target as it is already defined")
endif()
