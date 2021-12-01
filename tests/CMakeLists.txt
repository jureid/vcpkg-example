find_package(GTest REQUIRED)
include(GoogleTest)

set (TEST_SOURCE_FILES
	fib-tests.cpp
	main.cpp
	)

add_executable(fib_tests ${TEST_SOURCE_FILES})
target_link_libraries(fib_tests PRIVATE GTest::gtest)

gtest_discover_tests(fib_tests)