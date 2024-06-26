include(GoogleTest)

#
# NOTE: Add all test source files
#
set(APP_TEST_SOURCES "${APP_TEST_SOURCE_DIR}/enum_iterable_test.cpp" "${APP_TEST_SOURCE_DIR}/result_test.cpp"
                     "${APP_TEST_SOURCE_DIR}/tagged_type_test.cpp" "${APP_TEST_SOURCE_DIR}/version_test.cpp")

#
# NOTE: Declare a custom name for the test executable
#
set(PROJECT_UNIT_TEST_NAME "${PROJECT_NAME}-tests")

#
# NOTE: Add all test sources to the executable, and any other sources
#
add_executable(${PROJECT_UNIT_TEST_NAME} ${APP_TEST_SOURCES})

#
# NOTE: Link any libraries we need to the test executable. The most notable being
# the gtest_main library.
#
target_include_directories(${PROJECT_UNIT_TEST_NAME} PUBLIC ${APP_INCLUDE_DIR})
target_link_libraries(${PROJECT_UNIT_TEST_NAME} PRIVATE etl_project_options gtest gtest_main)

#
# NOTE: Signal google test to discover all tests
#
gtest_discover_tests(${PROJECT_UNIT_TEST_NAME})
