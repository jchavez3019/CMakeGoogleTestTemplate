project(CmakeGoogleTestTemplateProject CXX)

add_library(LibraryCode STATIC LibraryCode.cpp)

target_include_directories(LibraryCode
    PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/../include
)