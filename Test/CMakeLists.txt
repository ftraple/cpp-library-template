cmake_minimum_required(VERSION 3.10)

set(THIS ${PROJECT_NAME}Test)

set(SOURCE_FILES
    ../MyLibrary/Source/Foo.cpp
    FooTest.cpp
)

add_subdirectory(googletest)

include_directories(../MyLibrary/Include)

add_executable(${THIS} ${SOURCE_FILES})

# Share the version with the library code trough 
target_compile_definitions(${THIS} PRIVATE
    FOO_MAJOR_VERSION=${PROJECT_VERSION_MAJOR}
    FOO_MINOR_VERSION=${PROJECT_VERSION_MINOR}
)

target_link_libraries(${THIS} gtest_main)

add_test(NAME ${THIS} COMMAND ${THIS})

