cmake_minimum_required(VERSION 3.8)
project(open62541pp_vendor)

find_package(ament_cmake REQUIRED)

set(CMAKE_INSTALL_PREFIX "${CMAKE_INSTALL_PREFIX}" CACHE STRING "Install prefix" FORCE)

set(UAPP_BUILD_TESTS OFF CACHE BOOL "Disable tests" FORCE)
set(UAPP_BUILD_EXAMPLES OFF CACHE BOOL "Disable examples" FORCE)
set(UAPP_BUILD_DOCUMENTATION OFF CACHE BOOL "Disable docs" FORCE)
set(UAPP_INTERNAL_OPEN62541 ON CACHE BOOL "Use internal open62541" FORCE)

# we're probably using it in .so files, so we need PIC
set(CMAKE_POSITION_INDEPENDENT_CODE ON CACHE BOOL "Build with PIC" FORCE)

set(UA_ENABLE_ENCRYPTION "OPENSSL" CACHE STRING "Encryption provider" FORCE)

include(FetchContent)
FetchContent_Declare(
    open62541pp
    GIT_REPOSITORY  https://github.com/open62541pp/open62541pp.git
    GIT_TAG         master
    GIT_SHALLOW     true
)

FetchContent_MakeAvailable(open62541pp)

ament_package(
  CONFIG_EXTRAS "cmake/open62541pp_vendor-extras.cmake"
)