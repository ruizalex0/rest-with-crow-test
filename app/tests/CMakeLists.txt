add_executable(basic_test basic_test.cpp)
target_link_libraries(basic_test GTest::gtest_main)

include(GoogleTest)
gtest_discover_tests(basic_test)
