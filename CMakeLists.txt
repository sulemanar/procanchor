cmake_minimum_required(VERSION 3.10)

project(ProcAnchor VERSION 0.1.0)

set(PACKAGE_VERSION "0.1.0")
set(PACKAGE_HOMEPAGE_URL "")

option(ENABLE_TESTS "Build unit tests" OFF)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_definitions(-D_GNU_SOURCE)

if(ENABLE_TESTS)
  find_package(GTest REQUIRED)
endif()

configure_file(
  src/sysconfig.h.cmake
  ${CMAKE_CURRENT_BINARY_DIR}/src/sysconfig.h
)

include_directories(${CMAKE_CURRENT_BINARY_DIR}/src)

add_subdirectory(src)