cmake_minimum_required(VERSION 3.15)

project(ImarisWriterTest
  LANGUAGES C CXX
)

enable_testing()

include(ExternalProject)

ExternalProject_Add(ImarisWriter
  GIT_REPOSITORY https://github.com/imaris/ImarisWriter.git
  PREFIX ${CMAKE_BINARY_DIR}/Writer
)

add_subdirectory(application)

add_subdirectory(testC)
