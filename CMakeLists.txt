cmake_minimum_required(VERSION 3.21)
set(CMAKE_CXX_STANDARD 17)
project(vcpkg-example CXX)

include(CTest)

find_package(fmt CONFIG REQUIRED)
find_package(cppitertools CONFIG REQUIRED)

find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

add_executable(vcpkg-example src/main.cxx)
target_compile_features(vcpkg-example PRIVATE cxx_std_17)

target_link_libraries(vcpkg-example
  PRIVATE
    ${GTEST_LIBRARIES}
    fmt::fmt
    cppitertools::cppitertools)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

if (BUILD_TESTING)
    enable_testing()
    add_subdirectory(tests)
endif()