cmake_minimum_required(VERSION 3.15)

project(vcpkg-example CXX)

find_package(fmt REQUIRED)
find_package(range-v3 REQUIRED)
find_package(cxxopts REQUIRED)

add_executable(vcpkg-example src/main.cxx)
target_compile_features(vcpkg-example PRIVATE cxx_std_17)

target_link_libraries(vcpkg-example
  PRIVATE
    fmt::fmt
    range-v3::range-v3
    cxxopts::cxxopts)