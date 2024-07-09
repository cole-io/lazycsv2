cmake_minimum_required(VERSION 3.7)
project(testing)

set(CMAKE_CXX_STANDARD 20)

add_executable(main main.cpp)

# target_link_libraries(main lazycsv) not sure why this was here

target_include_directories(main SYSTEM PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/doctest)

add_custom_command(
  TARGET main
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E copy_directory ${CMAKE_CURRENT_SOURCE_DIR}/inputs
          ${CMAKE_CURRENT_BINARY_DIR}/inputs)

add_test(main main)
