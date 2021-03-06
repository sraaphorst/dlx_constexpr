# CMakeLists.txt
# By Sebastian Raaphorst, 2018.

cmake_minimum_required(VERSION 3.12)
project(dlx_constexpr_test)

# Enables testing from this directory downwards.
enable_testing(true)

# Prepare "Catch" library for other executables.
set(CATCH_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR})
add_library(Catch INTERFACE)
target_include_directories(Catch INTERFACE ${CATCH_INCLUDE_DIR})

# Make main executable that will be linked with other tests.
set(TEST_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp)
add_executable(tests ${TEST_SOURCES})
target_link_libraries(tests Catch)

add_executable(TestSmallCover TestSmallCover.cpp ${TEST_SOURCES})
add_executable(TestTDesign TestTDesign.cpp ${TEST_SOURCES})
add_executable(TestSudoku TestSudoku.cpp ${TEST_SOURCES})
