cmake_minimum_required(VERSION 3.17)
project(CmakeGoogleTestTemplateProject CXX)

#get googletest
include(FetchContent)
FetchContent_Declare(googletest 
    GIT_REPOSITORY https://github.com/google/googletest
    GIT_TAG v1.14.0
)
FetchContent_GetProperties(googletest)

#googletest_POPULATED
#googletest_SOURCE_DIR
#googletest_BUILD_DIR
if(NOT googletest_POPULATED)
    FetchContent_Populate(googletest)
    add_subdirectory(${googletest_SOURCE_DIR} ${googletest_BUILD_DIR})
endif()

option (BUILD_EXAMPLES "Whether or not to build examples"
ON)

option (BUILD_TESTS "Whether or not to build tests"
ON)

message(STATUS "Adding subdirectories")
add_subdirectory(include)
add_subdirectory(src)

if (BUILD_EXAMPLES)
    message(STATUS "Building examples...")
    add_subdirectory(example)
endif()

if (BUILD_TESTS)
    message(STATUS "Building tests...")
    enable_testing()
    add_subdirectory(tests)
endif()