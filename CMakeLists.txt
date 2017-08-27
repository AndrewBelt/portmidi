# portmidi
# Roger B. Dannenberg
# 20 Sep 2009

cmake_minimum_required(VERSION 3.0)

project(portmidi)


if(UNIX)
  # allow user to set Release or Debug
  set(CMAKE_BUILD_TYPE Release CACHE STRING
      "Semicolon-separate list of supported configuration types")
  # set default directories but don't override cached values...

else(UNIX)
  # this does not seem to work for xcode:
  set(CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING
      "Semicolon-separate list of supported configuration types")
endif(UNIX)

#set(CMAKE_RELATIVE_PATHS ON CACHE STRING "avoid absolute paths" FORCE)

# Clear out the built-in C++ compiler and link flags for each of the
# unused configurations.
set(CMAKE_CXX_FLAGS_MINSIZEREL "" CACHE INTERNAL "Unused")
set(CMAKE_SHARED_LINKER_FLAGS_MINSIZEREL "" CACHE INTERNAL "Unused")
set(CMAKE_MODULE_LINKER_FLAGS_MINSIZEREL "" CACHE INTERNAL "Unused")
set(CMAKE_EXE_LINKER_FLAGS_MINSIZEREL "" CACHE INTERNAL "Unused")
set(CMAKE_CXX_FLAGS_RELWITHDEBINFO "" CACHE INTERNAL "Unused")
set(CMAKE_SHARED_LINKER_FLAGS_RELWITHDEBINFO "" CACHE INTERNAL "Unused")
set(CMAKE_MODULE_LINKER_FLAGS_RELWITHDEBINFO "" CACHE INTERNAL "Unused")
set(CMAKE_EXE_LINKER_FLAGS_RELWITHDEBINFO "" CACHE INTERNAL "Unused")

set(CMAKE_OSX_ARCHITECTURES i386 ppc x86_64 CACHE STRING "change to needed architecture for a smaller library" FORCE)


include_directories(pm_common porttime)

add_subdirectory(pm_common)
add_subdirectory(pm_test)
