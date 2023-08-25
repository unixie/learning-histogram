cmake_minimum_required(VERSION 3.25 FATAL_ERROR)

project(
  learn-histogram
  VERSION 1.0
  LANGUAGES CXX
  )

# CXX global configuration
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)


# === CMake includes ==========================================================
# Basic project checks
include(cmake/guard.cmake)
# Include debugging utilities
include(CMakePrintHelpers)


# === Dependencies ============================================================
include(cmake/CPM.cmake)

CPMAddPackage(
  NAME CLI11
  GIT_TAG v2.3.2
  GITHUB_REPOSITORY CLIUtils/CLI11
)

CPMAddPackage(
  NAME fmt
  GIT_TAG 9.1.0
  GITHUB_REPOSITORY fmtlib/fmt
)

set(Boost_USE_DEBUG_LIBS        OFF)
set(Boost_USE_RELEASE_LIBS       ON)
set(Boost_USE_MULTITHREADED      ON)
set(Boost_USE_STATIC_LIBS        ON)
set(Boost_DEBUG                 OFF) # enable to debug underlying FindBoost
# Explicitly list dependencies, even header-only
set(BOOST_INCLUDE_LIBRARIES     histogram)
CPMAddPackage(
  NAME Boost
  VERSION 1.82.0
  GITHUB_REPOSITORY "boostorg/boost"
  GIT_TAG "boost-1.82.0"
  EXCLUDE_FROM_ALL YES
)


# === Project tree ============================================================
add_subdirectory(lib)
add_subdirectory(apps)
