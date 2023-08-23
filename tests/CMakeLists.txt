project(CmakeGoogleTestTemplateProject CXX)

add_executable(test_one test_one.cpp)

target_link_libraries(test_one
    PUBLIC
    LibraryCode
    gtest_main
    gmock_main
)

add_test(
    NAME test_one
    COMMAND test_one
)